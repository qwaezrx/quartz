---
tags:
  - CS/Programming/Python/PyTorch/Torchvision
---


```python
from torchvision import models
from torchvision.models.resnet import ResNet18_Weights

model = models.resnet18(ResNet18_Weights)

```

## See more
- https://pytorch.org/vision/main/models.html