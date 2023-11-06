

```python
def evaluate_toxicity(model,
					  toxicity_evaluator,
					  tokenizer,
					  dataset,
					  num_samples,
					  max_new_tokens=100,
					  top_k=0.0,
					  top_p=1.0):
	"""
	Preprocess the dataset and split it into train and test parts.
	
	Parameters:
	- model (trl model): Model to be evaluated.
	- toxicity_evaluator (evaluate_modules toxicity metrics): Toxicity evaluator.
	- tokenizer (transformers tokenizer): Tokenizer to be used.
	- dataset (dataset): Input datasetfor the evaluation.
	- num_samples (int): Maximum number of samples for the evaluation.
	
	Returns:
	tuple: A tuple containing two numpy.float64 values:
	- mean (numpy.float64): Mean of the samples toxicity.
	- std (numpy.float64): Standard deviation of the samples toxicity.
	"""
	
	toxicities = []
	input_texts = []
	for i, sample in tqdm(enumerate(dataset)):
		input_text = sample["query"]
		
		if i > num_samples:
			break
			
		input_ids = tokenizer(input_text, return_tensors="pt", padding=True).input_ids
			
		generation_config = GenerationConfig(
			max_new_tokens=max_new_tokens,
			top_k=top_k,
			top_p=top_p,
			do_sample=True
		)
		
		response_token_ids = model.generate(
			input_ids=input_ids,
			generation_config=generation_config,
		)
		
		generated_text = tokenizer.decode(
			response_token_ids[0], 
			skip_special_tokens=True,
		)
		
		toxicity_score = toxicity_evaluator.compute(
			predictions=[(input_text + " " + generated_text)]
		)
		
		toxicities.extend(toxicity_score["toxicity"])
	
	# Compute mean & std using up.
	mean = np.mean(toxicities)
	std = np.std(toxicities)
	
	return mean, std

```
