---
tags:
  - CS/Programming/Python/PyTorch
---

[[torch.utils.data.Dataset]] -> class Data(Dataset):

#### LR; Mini-Batch Gradient Descent with PyTorch
```python
from torch.utils.data import DataLoader

dataset = Data()

trainloader = DataLoader(dataset=dataset, batch_size=1)
```

```python
for x, y in trainloader:
	yhat = forward(x)
	loss = criterion(yhat, y)
	loss.backward()

	...
```

