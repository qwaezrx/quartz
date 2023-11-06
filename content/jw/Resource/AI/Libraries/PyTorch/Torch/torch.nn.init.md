---
tags:
  - CS/Programming/Python/PyTorch
---

#### Xavier (with tanh)
```python
import torch
import torch.nn as nn

linear = nn.Linear(input_size, output_size)

torch.nn.init.xavier_uniform_(linear.weight)
```

![[Screenshot 2023-09-09 at 4.53.32 AM.png]]

#### He (with ReLU)
```python
torch.nn.init.kaiming_uniform_(linear.weight, nonlinearity='relu')
```

```python
class Net_He(nn.Module):
	def __init__(self, Layers):
		super(Net_He, self).__init__()
		self.hidden = nn.ModuleList()

		for input_size, output_size in zip(Layers, Layers[1:]):
			linear = nn.Linear(input_size, output_size)
			torch.nn.init.kaiming_uniform_(linear.weight, nonlinearity='relu')
			self.hidden.append(linear)

	def forward(self, x):
		L = len(self.hidden)
		for (l, linear_transform) in zip(range(L), self.hidden):
			if l < L - 1:
				x = F.relu(linear_transform(x))
			else:
				x = linear_transform(x)

		return x
```

