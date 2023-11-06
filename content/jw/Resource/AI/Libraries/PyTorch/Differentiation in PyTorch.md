---
tags:
  - CS/Programming/Python/PyTorch
---

```python
import torch
import matplotlib.pylab as plt
```

```python

x = torch.tensor(2.0, requires_grad=True)
print("The tenser x: ", x)
```

```python
y = x ** 2

y.backward()
print("The derivative at x = 2: ", x.grad)
```


```python
class SQ(torch.autograd.Function):

	@staticmethod
	def forward(ctx, i):
		result = i ** 2
		ctx.save_for_backward(i)
		return result

	@staticmethod
	def backward(ctx, i):
		i, = ctx.saved_tensors
		grad_output = 2 * i
		return grad_output
```

```python
x = torch.tensor(2.0, requires_grad=True)
sq = SQ.apply

y = sq(x)
y.backward()

print(x.grad)
```