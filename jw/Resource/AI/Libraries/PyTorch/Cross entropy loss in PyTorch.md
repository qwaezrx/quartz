---
tags:
  - CS/Programming/Python/PyTorch
---

Advantage of [[Cross Entropy Loss]]:
- The only flat point is at the minimum

Why not using MSE:
- During training, you may not reach the minimum of the cost surface

```python
import torch

def criterion(yhat, y):
	out = -1 * torch.mean(y * torch.log(yhat) + (1 - y) * torch.log(1 - yhat))
	return out
```

```python
import torch.nn as nn

criteria = nn.BCELoss()

```