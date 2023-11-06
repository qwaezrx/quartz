---
tags:
  - CS/Programming/Python/PyTorch/Torchvision
---


```python
class torchvision.datasets.ImageFolder(
	root: str,
	transform: typing.OPtional[~typing.Callable] = None,
	target_transform: typing.Optional[~typing.Callable] = None,
	loader: ~typing.Callable[[str], ~typing.Any] = default_loader,
	is_valid_file = None
)
```

A generic data loader where the images are arranged in this way by default:
```
root/dog/xxx.png
root/dog/xxy.png
root/dog/[...]/xxz.png

root/cat/123.png
root/cat/nsdf3.png
root/cat/[...]/asd932_.png
```



## See more
- https://pytorch.org/vision/stable/generated/torchvision.datasets.ImageFolder.html