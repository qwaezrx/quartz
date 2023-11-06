---
tags:
  - CS/Programming/Python/PyTorch
---

```python
import torch
import torch.nn as nn
import torchvision.transforms as transforms
import torchvision.datasets as dsets

train_dataset = dsets.MNIST(root='./data', train=True, download=True, transform=transform.ToTenser())
test_dataset = dsets.MNIST(root='./data', train=False, download=True, transform=transform.ToTensor())
```



