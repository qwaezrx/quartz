---
tags:
  - AI/Fine-Tuning
  - AI/GAI/LLM
---



# 1. Install and import dependencies

```python
%pip install --upgrade pip
%pip install --disable-pip-version-check \
	torch==1.13.1 \
	torchdata==0.5.1 --quite

%pip install \
	transformers==4.27.2 \
	datasets==2.11.0 \
	evaluate==0.4.0 \
	rouge_score==0.1.2 \
	peft==0.3.0 --quite 

# Installing the Reinforcement Learning library directly from github.
%pip install git+https://github.com/lvwerra/trl.git@25fa1bd    
```

```python
from transformers import pipeline, AutoTokenizer, AutoModelForSequenceClassification, AutoModelForSeq2SeqLM, GenerationConfig
from datasets import load_dataset
from peft import PeftModel, PeftConfig, LoraConfig, TaskType

# trl: Transformer Reinforcement Learning library
from trl import PPOTrainer, PPOConfig, AutoModelForSeq2SeqLMWithValueHead
from trl import create_reference_model
from trl.core import LengthSampler

import torch
import evaluate

import numpy as np
import pandas as pd

# tqdm library makes the loops show a smart progress meter.
from tqdm import tqdm
tqdm.pandas()
```

# 2. Load FLAN-T5 Model, Prepare Reward Model and Toxicity Evaluator

## 2.1 - Load data and FLAM-T5 Model Fine-Tuned with Summarization Instruction

```python
model_name="google/flan-t5-base"
huggingface_dataset_name="knkarthick/dialogsum"

dataset_original = load_dataset(huggingface_dataset_name)

dataset_original
```

```python
def build_dataset(model_name,
				  dataset_name,
				  input_min_text_length,
				  input_max_text_length):
	"""
	Preprocess the dataset and split it into train and test parts.

	Parameters:
	- model_name (str): Tokenizer model name.
	- dataset_name (str): Name of the dataset to load.
	- input_min_text_length (int): Minimum length of the dialogues.
	- input_max_text_length (int): Maximum length of the dialogques.

	Returns:
	- dataset_splits (datasets.dataset_dict.DatasetDict): Preprocessed dataset containing train and test parts.
	"""

	# load dataset (only "train" part will be enough for this lab).
	dataset = load_dataset(dataset_name, split="train")

	# Filter the dialogues of length between input_min_text_length and input_max_text_length characters.
	dataset = dataset.filter(lambda x: len(x["dialogue"]) > input_min_text_length and len(x["dialogue"]) <= input_max_text_length, batched=False)

	# Prepare tokenizer. Setting device_map="auto" allows to switch between GPU and CPU automatically.
	tokenizer = AutoTokenizer.from_pretrained(model_name, device_map="auto")

	def tokenize(sample):
		
		# Wrap each dialogue with the instruction.
		prompt=f"""
Summarize the following convention.

{sample["dialogue"]}

Summary:
"""
		sample["input_ids"] = tokenizer.encode(prompt)
			
		# This must be called "query", which is a requirement of out PPO library.
		sample["query"] = tokenizer.decode(sample["input_ids"])
		return sample
	
	# Tokenize each dialogue.
	dataset = dataset.map(tokenize, batched=False)
	dataset.set_format(type="torch")
	
	# Split the dataset into train and test parts.
	dataset_splits = dataset.train_test_split(test_size=0.2, shuffle=False, seed=42)
	
	return dataset_splits


dataset = build_dataset(model_name=model_name,
						dataset_name=dataset_name,
						input_min_text_length=200,
						input_max_text_length=1000)

print(dataset)
```

```
DatasetDict({
    train: Dataset({
        features: ['id', 'dialogue', 'summary', 'topic', 'input_ids', 'query'],
        num_rows: 8017
    })
    test: Dataset({
        features: ['id', 'dialogue', 'summary', 'topic', 'input_ids', 'query'],
        num_rows: 2005
    })
})
```

[[def get_trainable_parameters_num]]

```python
lora_config = LoraConfig(
	r=32, # Rank
	lora_alpha=32,
	target_modules=["q", "v"],
	lora_dropout=0.05,
	bias="none",
	task_type=TaskType.SEQ_2_SEQ_LM # FLAN-T5
)

model = AutoModelForSeq2SeqLM.from_pretrained(
	model_name,
	torch_dtype=torch.bfloat16
)

peft_model = PeftModel.from_pretrained(
	model,
	'./peft-dialogue-summary-checkpoint-from-s3/',
	lora_config=lora_config,
	torch_dtype=torch.bfloat16,
	device_map="auto",
	is_trainable=True,
)

```

```python
ppo_model = AutoModelForSeq2SeqLMWithValueHead.from_pretained(
	peft_model,
	torch_dtype=torch.bfloat16,
	is_tainable=True,
)
```

```python
ref_model = create_reference_model(ppo_model)
```

## 2.2 - Prepare Reward Model

```python
toxicity_model_name = "facebook/roberta-hate-speech-dynabench-r4-target"
toxicity_tokenizer = AutoTokenizer.from_pretrained(toxicity_model_name, device_map="auto")
toxicity_model = AutoModelForSequenceClassification.from_pretrained(toxicity_model_name, device_map="auto")
print(toxicity_model.config.id2label)
```

```python
non_toxic_text = "#Person 1# tells Tommy that he didn't like the movie."
toxicity_input_ids = toxicity_tokenizer(non_toxic_text, return_tensors="pt").input_ids

logits = toxicity_model(input_ids=toxicity_input_ids).logits
print(f"logits [nothate, hate]: {logits.tolist()[0]}")

# Print the probabilities for [not hate, hate]
probabilities = logits.softmax(dim=-1).tolist()[0]
print(f"probabilities [not hate, hate]: {probabilities}")

# get the logits for "not hate" - this is the reward!
not_hate_index = 0
nothate_reward = (logits[:, not_hate_index]).tolist()
print(f"reward (high): {nothate_reward}")
```

```python
toxic_text = "#Person 1# tells Tommy that the movie was terrible, dumb and stupid."

toxicity_input_ids = toxicity_tokenizer(toxic_text, return_tensors="pt").input_ids

logits = toxicity_model(toxicity_input_ids).logits
print(f'logits [not hate, hate]: {logits.tolist()[0]}')

# Print the probabilities for [not hate, hate]
probabilities = logits.softmax(dim=-1).tolist()[0]
print(f'probabilities [not hate, hate]: {probabilities}')

# Get the logits for "not hate" - this is the reward!
nothate_reward = (logits[:, not_hate_index]).tolist() 
print(f'reward (low): {nothate_reward}')
```

```python
device = 0 if torch.cuda.is_available() else "cpu"

sentiment_pipe = pipeline("sentiment-analysis",
						 model=toxicity_model_name,
						 device=device)
reward_logits_kwargs = {
	"top_k": None, # Return all scores.
	"function_to_apply": "none", # Set to "none" to retrieve raw logits.
	"batch_size": 16
}

reward_probabilities_kwargs = {
	"top_k": None, # Return all scores.
	"function_to_apply": "softmax", # Set to "softmax" to apply softmax and retrieve probabilities.
	"batch_size": 16
}

print("Reward model output:")
print("For non-toxic text")
print(sentiment_pipeline(non_toxic_text, **reward_logits_kwargs))
print(sentiment_pipeline(non_toxic_text, **reward_probabilities_kwargs))

print("For toxic text")
print(sentiment_pipeline(toxic_text, **reward_logits_kwargs))
print(sentiment_pipelint(toxic_text, **reward_probabilities_kwargs))
```

## 2.3 - Evaluate Toxicity
```python
toxicity_evaluator = evaluate.load("toxicity",
								  toxicity_model_name,
								  module_type="measurement",
								  toxic_label="hate")

```

```python
toxicity_score = toxicity_evaluator.compute(predictions=[
	non_toxic_text
])

print("Toxicity score for non-toxic text:")
print(toxicity_score["toxicity"])

toxicity_score = toxicity_evaluator.compute(predictions=[
	toxic_text
])

print("\nToxicity score for toxic text:")
print(toxicity_score["toxicity"])
```

[[def evaluate_toxicity]]

```python
tokenizer = AutoTokenizer.from_pretrained(model_name, device_map="auto")

mean_before_detoxication, std_before_detoxication = evaluate_toxicity(													model=ref_model, 
	toxicity_evaluator=toxicity_evaluator,
	tokenizer=tokenizer,
	dataset=dataset["test"],
	num_samples=10)

print(f'toxicity [mean, std] before detox: [{mean_before_detoxification}, {std_before_detoxification}]')
```

# 3 - Perform Fine-Tuning to Detoxify the Summaries

## 3.1 - Initialize PPOTrainer
```python
def collator(data):
	return dict((key, [d[key] for d in data]) for key in data[0])
```


```python
learning_rate = 1.41e-5
max_ppo_epochs = 1
mini_batch_size = 4
batch_size = 16

config = PPOConfig(
	model_name=model_name,
	learning_rate=learning_rate,
	ppo_epochs=max_ppo_epochs,
	mini_batch_size=mini_batch_size,
	batch_size=batch_size,
)

ppo_trainer = PPOTrainer(config=config
						 model=ppo_model,
						 ref_model=ref_model,
						 tokenizer=tokenizer,
						 dataset=dataset["train"],
						 data_collator=collator)
```


## 3.2 - Fine-Tune the Model
```python
output_min_length = 100
output_max_length = 400
output_length_sampler = LengthSampler(output_min_length, output_max_length)

generation_kwargs = {
	"min_length": 5,
	"top_k": 0.0,
	"top_p": 1.0,
	"do_sample": True,
}

reward_kwargs = {
	"top_k": None, # Return all scores.
	"function_to_apply": "none", # You want raw logits without softmax.
	"batch_size": 16,
}

max_ppo_steps = 10

for step, batch in tqdm(enumerate(ppo_trainer.dataloader)):
	# Break when you reach max_steps.
	if step >= max_ppo_steps:
		break
	
	prompt_tensors = batch["input_ids"]
	
	# Get response from FLAN-T5/PEFT LLM.
	summary_tensors = []
	
	for prompt_tensor in prompt_tensors:
		max_new_tokens = output_length_sampler()
		
		generation_kwargs["max_new_tokens"] = max_new_tokens
		summary = ppo_trainer.generate(
			prompt_tensor, **generation_kwargs
		)
		
		summary_tensors.append(
			summary.squeeze()[-max_new_tokens:]
		)
	
	# This needs to be called "response".
	batch["response"] = [tokenizer.decode(r.squeeze()) for r in summary_tensors]
	
	# Compute reward outputs.
	query_response_pairs = [q * r for q, r in zip(batch["query"], batch["response"])]
	rewards = sentiment_pipe(query_response_pairs, **reward_kwargs)
	
	# You use the `nothate` item because this is the score fot the positive `nothate` class.
	reward_tensors = [torch.tensor(reward[not_hate_index]["score"]) for reward in rewards]
	
	# Run PPO step.
	stats = ppo_trainer.step(prompt_tensors, summary_tensors, reward_tensors)
	
	ppo_trainer.log_stats(stats, batch, reward_tensors)
	
	print(f'objective/kl: {stats["objective/kl"]}')
    print(f'ppo/returns/mean: {stats["ppo/returns/mean"]}')
    print(f'ppo/policy/advantages_mean: {stats["ppo/policy/advantages_mean"]}')
    print('-'.join('' for x in range(100)))

```

## 3.3 - Evaluate the Model Quantitatively
```python
mean_after_detoxication, std_after_detoxication = evaluate_toxicity(
	model=ppo_model,
	toxicity_evaluator=toxicity_evaluator,
	tokenizer=tokenizer,
	dataset=dataset["test"],
	num_samples=10)

print(f'toxicity [mean, std] after detox: [{mean_after_detoxification}, {std_after_detoxification}]')
```

## 3.4 - Evaluate the Model Qualitatively
```python
batch_size = 20
compare_results = {}

df_batch = dataset["test"][0:batch_size]

compare_results["query"] = df_batch["query"]
prompt_tensors = df_batch["input_ids"]

summary_tensors_ref = []
summary_tensors = []

# Get response from ppo and base model.
for i in tqdm(range(batch_size)):
	gen_len = output_length_sampler()
	generation_kwargs["max_new_tokens"] = gen_len
	
	summary = ref_model.generate(
		input_ids=torch.as_tensor(
			prompt_tensors[i]
		).unsqueeze(dim=0).to(device),
		**generation_kwargs,
	).squeeze()[-gen_len:]
	
	summary_tensors_ref.append(summary)
	
	summary = ppo_model.generate(
		input_ids=torch.as_tensor(
			prompt_tensors[i]
		).unsqueeze(dim=0).to(device),
		**generation_kwargs,
	).squeeze()[-gen_len:]
	
	summary_tensors.append(summary)

# Decode responses.
compare_results["response_before"] = [
	tokenizer.decode(summary_tensors_ref[i]) for i in range(batch_size)
]
compare_results["response_after"] = [
	tokenizer.decode(summary_tensors[i]) for i in range(batch_size)
]

# Sentiment analysis of query/response pairs before/after.
texts_before = [d + s for d, s in zip(compare_results["query"], compare_results["response_before"])]
rewards_before = sentiment_pipeline(texts_before, **rewards_kwargs)
compare_results["reward_before"] = [reward[not_hate_index]["score"] for reward in rewards_before]

texts_after = [d + s for d, s in zip(compare_results["query"], compare_results["response_after"])]
rewards_after = sentiment_pipeline(texts_after, **rewards_kwargs)
compare_results["reward_after"] = [reward[not_hate_index]["score"] for reward in rewards_after]

```


```python
pd.set_option('display.max_colwidth', 500)
df_compare_results = pd.DataFrame(compare_results)
df_compare_results["reward_diff"] = df_compare_results['reward_after'] - df_compare_results['reward_before']
df_compare_results_sorted = df_compare_results.sort_values(by=['reward_diff'], ascending=False).reset_index(drop=True)
df_compare_results_sorted
```

