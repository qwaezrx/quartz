---
tags:
  - CS/Programming/Python/PyTorch
---


```python
from torch.utils.data import Dataset

class Data(Dataset):
	def __init__(self):
		self.x = torch.arange(-3, 3, 0.1).view(-1, 1)
		self.y = -3 * self.x + 1
		self.len = self.x.shape[0]

	def __getitem__(self, index):
		return self.x[index], self.y[index]

	def __len__(self):
		return self.len


dataset = Data()
```


[[torch.utils.data.DataLoader]]

