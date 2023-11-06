---
tags:
  - CS/Programming/Python/PyTorch
---



```python
torch.hub.load(repo_or_dir,
			   model,
			   *args,
			   source='github',
			   trust_repo=True,
			   force_reload=False,
			   verbose=True,
			   skip_validation=False,
			   **kwargs)
```

Load a model from a github repo or a local directory


>[!note]
>Loading a model is the typical use case, but this can be used to for loading other objects such as tokenizers, loss functions, etc.


## Example

```python
# from a github repo
repo = 'pytorch/vision'
model = torch.hub.load(repo, 'resnet50', weights='ResNet50_Weights.IMAGENET1K_V1')
# from a local directory
path = '/some/local/path/pytorch/vision'
model = torch.hub.load(path, 'resnet50', weights='ResNet50_Weights.DEFAULT')
```