---
tags:
  - CS/Programming/Python/PyTorch
---


```python
import torch.nn as nn

dropout = nn.Dropout(p=0.1)
```

When training:
```python
model.train()
yhat = model(x)
```

When evaluating:
```python
model.eval()
yhat = model(x)
```

