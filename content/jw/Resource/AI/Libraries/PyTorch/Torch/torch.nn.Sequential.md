---
tags:
  - CS/Programming/Python/PyTorch
---


```python
import torch.nn as nn

sequential_model = nn.Sequential(
	nn.Linear(1, 1),
	nn.Sigmoid(),
)
```

