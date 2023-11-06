---
tags:
  - CS/Programming/Python/PyTorch
---

#### Stochastic gradient descent


```python
def forward(x):
	y = w * x + b
	return y

def criterion(yhat, y):
	return torch.mean((yhat - y) ** 2)
```

```python

lr = 0.1

costs = []

for epoch in range(3):
	Yhat = forward(X)
	loss = criterion(Yhat, Y)
	loss.backward()

	w.data = w.data - lr * w.grad.data
	w.grad.data.zero_()

	b.data = b.data - lr * b.grad.data
	b.grad.data.zero_()
	
	cost.append(loss.item())
```


#### Mini-Batch gradient descent
[[torch.utils.data.DataLoader#LR; Mini-Batch Gradient Descent with PyTorch]]




