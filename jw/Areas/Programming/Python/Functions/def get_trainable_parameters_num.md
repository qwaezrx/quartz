

```python
def get_trainable_model_parameters_count(model):
	trainable_model_params = 0
	all_model_params = 0
	for _, param in model.named_parameters():
		all_model_params += param.numel()
		if param.requires_grad:
			trainable_model_params += param.numel()
	return trainable_model_params
```
