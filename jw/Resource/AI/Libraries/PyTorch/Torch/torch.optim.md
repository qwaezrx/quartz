---
tags:
  - CS/Programming/Python/PyTorch
---


```python
from torch import optim as optim

optimizer = optim.SGD(model.parameters(), lr=0.01)

optimzier.state_dict()
```


```python
for epoch in range(100):
	for x, y in trainloader:
		yhat = model(x)
		loss = criterion(yhat, y)
		optimizer.zero_grad()
		loss.backward()
		optimizer.step()
```

![[Screenshot 2023-09-09 at 1.43.53 AM.png]]