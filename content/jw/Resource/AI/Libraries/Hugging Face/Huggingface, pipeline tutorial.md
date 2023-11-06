---
tags:
  - CS/Programming/Python/Huggingface
---


## Pipelines for inference
The `pipeline()` makes it simple to use any model from the Hub for inference on any language, computer vision, speech and multimodal tasks.

## Pipeline usage
While each task has an associated `pipeline()`, it is simpler to use the general `pipeline()` abstraction which contains all the task-specific pipelines. The `pipeline()` automatically loads a default model and a preprocessing class capable of inference fro your task.

1. Start by creating a `pipeline()` and specify an inference task:
```python
from transformers import pipeline

generator = pipeline(task="automatic-speech-recognition")
```

2.  Pass your input text to the `pipeline()`:

- Using default model:
```python
generator("https://huggingface.co/datasets/Narsil/asr_dummy/resolve/main/mlk.flac")

# {'text': 'I HAVE A DREAM BUT ONE DAY THIS NATION WILL RISE UP THE TRUE MEANING OF ITS TREES'}
```

- Using openai/whisper-large:
```python
generator = pipeline(model="openai/whisper-large")

generator("https://huggingface.co/datasets/Narsil/asr_dummy/resolve/main/mlk.flac")
# {'text': 'I have a dream that one day this nation will rise up and live out the true meaning of its creed.'}
```

- If you have several inputs, you can pass your input as list:
```python
generator(
    [        "https://huggingface.co/datasets/Narsil/asr_dummy/resolve/main/mlk.flac",
"https://huggingface.co/datasets/Narsil/asr_dummy/resolve/main/1.flac",
    ]
)
```

- If you want to iterate over a whole dataset, or want to use it for inference in a webserver, check out dedicated parts
	- [Using pipelines on a dataset](https://huggingface.co/docs/transformers/pipeline_tutorial#using-pipelines-on-a-dataset)
	- [Using pipelines for a webserver](https://huggingface.co/docs/transformers/pipeline_webserver)

## Parameters
`pipeline()` supports many parameters, some are task specific, and some are general to all pipelines. In general you can specify parameters anywhere you want:
```python
generator = pipeline(model="openai/whisper-large", my_parameter=1)
output = generator(...) # This will use `my_parameter=1`
output = generator(..., my_parameter=2) # This will override and use `my_parameter=2`.
	output = generator(...) # This will go back to using `my_parameter=1`
```

3 Important parameters are:
### Device
if you use device=n, the pipeline automatically puts the model on the specified device. This will work regardless of whether you are using [[PyTorch]] or [[Tensorflow]].
```python
generator = pipeline(model="openai/whisper-large" device=0)
```

if the model is too large for single [[GPU]], you can set `device_map="auto"` to allow [[Accelerate]] to automatically determine how to load and store the model weights.
```python
#!pip install accelerate
generator = pipeline(model="openai/whisper-large", device_map="auto")
```

>[!note]
>If `device_map="auto"` is passed, there is no need to add the argument `device=device` when instantiating your `pipeline` as you may encounter some unexpected behavior

### Batch size
By default, pipelines will not batch inference for reasons explained in detail  [here](https://huggingface.co/docs/transformers/main_classes/pipelines#pipeline-batching). The reason is that batching is not necessarily faster, and can actually be quite slower in some cases.

But if it works in your case, you can use:
```python
generator = pipeline(
	model="openai/whisper-large", 
	device=0, 
	batch_size=2
)
audio_filenames = [f"audio_{i}.flac" for i in range(10)]
texts = generator(audio_filenames)
```
>[!note]
>The output should always match what you would have received without batching.

Pipelines can also alleviate some of the complexities of batching because, for some pipelines, a single item (like a lone audio file) needs to be chunked into multiple parts to be processed by a model. The pipeline performs this [_chunk batching_](https://huggingface.co/docs/transformers/main_classes/pipelines#pipeline-chunk-batching) for you.

### Task specific parameters
All tasks provide task specific parameters which allow for additional flexibility and options to help you get your job done.
```python
generator = pipeline(model="facebook/wav2vec2-large-960h-1v60-self", return_timestamp="word")
...
```

## Using pipelines on a dataset
The pipeline can also run inference on a large dataset. The easiest way we recommend doing this is by using an iterator:
```python
def data():
	for i in range(1000):
		yield f"My example {i}"

pipe = pipeline(model="gpt2", device=0)
generated_characters = 0
for out in data():
	generated_characters += len(out[0]["generated_text"])
```

The iterator `data()` yields each result, and the pipeline automatically recognizes the input is iterable and will start fetching the data while it continues to process it on the GPU (this uses [[DataLoader]] under the hood).
>[!important]
>You don't have to allocate memory for the whole dataset and you can fed the GPU as fast as possible.

Since batching could speed things up, it may be useful to try tuning the batch_size parameter here.

The simplest way to iterate over a dataset is to just load one from 🤗 [Datasets](https://github.com/huggingface/datasets/):
```python
from transformers.pipelines.pt_utils import KeyDataset
from datasets import load_dataset

pipe = pipeline(model="hf-internal-testing/tiny-random-wav2vec2", device=0)
dataset = load_dataset("hf-internal-testing/librispeech_asr_dummy", "clean", split="validation[:10]")

for out in pipe(KeyDataset(dataset, "audio")):
	print(out)
```

## Using pipelines for a webserver
- [How to create an inference engine](https://huggingface.co/docs/transformers/pipeline_webserver)

## Vision pipeline
Using `pipeline()` for vision tasks is practically identical

Specify your task and pass your image to the classifier. The image can be a link or a local path to the image.
```python
from transformers import pipeline

vision_classifier = pipeline(model="google/vit-base-patch16-224")
preds = vision_classifier(
	images="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/pipeline-cat-chonk.jpeg"
)
preds = [{"score": round(pred["score"]), "label": pred["label"]} for pred in preds]

```

## Text pipeline
Using a `pipeline()` for [[NLP]] tasks is practically identical

```python
from transformers import pipeline

# This model is a `zero-shot-classification` model
# It will classify text, except you are free to choose any label you might imagine
classifier = pipeline(model="facebook/bart-large-mnli")
classifier(
	"I have a problem with my iphone that needs to be resolved asap!",
	candidate_labels=["urgent", "not urgent", "phone", "tablet", "computer"],
)

# {'sequence': 'I have a problem with my iphone that needs to be resolved asap!!', 'labels': ['urgent', 'phone', 'computer', 'not urgent', 'tablet'], 'scores': [0.504, 0.479, 0.013, 0.003, 0.002]}

```

## Multimodel pipeline
The `pipeline()` supports more than one modality. For example, a visual question answering ([[VQA]]) task combines text and image. Feel free to use any image link you like and a question you want to ask about the image. The image can be a URL or a local path to the image.

For example, if you use this invoice image:
```python
from transformers import pipeline

vqa = pipeline(model="impira/layout-document-qa")
vqa(
	image="https://huggingface.co/spaces/impira/ \
		docquery/resolve/2359223c1837a758740 \
		2bda0f2643382a6eefeab/invoice.png",
	question="What is the invoice number?",
)

# [{'score': 0.42515, 'answer': 'us-001', 'start': 16, 'end': 16}]
```

> [!note]
> To run the example above you need to have `pytesseract` installed:
> `sudo apt install -y tesseract-ocr`
> `pip install pytessaract`

## Using `pipeline` on large models with 🤗 `accelerate`:
You can easily run pipeline on large models using 🤗 `accelerate`.
1. Make sure you have installed `accelerate` with `pip install accelerate`
2. Load you model using `device_map="auto"`
```python
import torch
from transformers import pipeline

pipe = pipeline(model="facebook/opt-1.3b", torch_dtype=torch.bfloat16, device_map="auto")
output = pipe("This is a cool example!", do_sample=True, top_p=0.95)
```

- You can also pass 8-bit loaded models if you install `bitsandbytes` and add the argument `load_in_8bit=True`
```python
import torch 
from transformers import pipeline

pipe = pipeline(model="facebook/opt-1.3b", device_map="auto", model_kwargs={"load_in_8bit": True})
output = pipe("This is a cool example!", do_sample=True, top_p=0.95)
```

>[!note]
>You can replace the checkpoint with any of the [[Hugging Face]] model that supports large model loading such as [[BLOOM]]!





## See more
- https://huggingface.co/docs/transformers/pipeline_tutorial
- [pipeline()](https://huggingface.co/docs/transformers/v4.31.0/en/main_classes/pipelines#transformers.pipeline) documentation

