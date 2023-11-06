---
tags:
  - AI/Logistic_Regression
  - CS/Programming/Python/PyTorch
---


```python
import torch
from torch.nn import Linear
```

```python
lr = Linear(in_features=1, out_features=1, bias=True)
print("Parameters w and b: ", list(lr.parameters()))
```

```python
x = torch.tensor([[1.0]])
yhat = lr(x)
print(yhat)
```

```python
import torch.nn as nn

class LR(nn.Module):
	def __init__(self, input_size, output_size):
		super(LR, self).__init__()
		self.linear = nn.Linear(input_size, output_size)

	def forward(self, x):
		out = self.linear(x)
		return out
```

```python
lr = LR(1, 1)
print("The parameters: ", list(lr.parameters()))
```

```python
print("Python dictionary: ", lr.state_dict())
```

## LR training with torch
- [[LR; Gradient descent in PyTorch]]
