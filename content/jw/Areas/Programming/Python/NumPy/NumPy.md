---
tags:
  - CS/Programming/Python/NumPy
---

```python
import numpy as np

# rank 1 array
a = np.random.randn(5)
# a.shape = (5, ) "rank 1 array"
print(a)
print(a.shape)
```

>[!warning]
>Do not use use __Rank 1__ array.
>
>For example, don't use np.random.randn(5),
>use column vector: np.random.randn(5, 1) or
>use row vector: np.random.randn(1, 5) instead

```python
print(a.T)
```

```python
print(np.dot(a, a))
```

```python
b = np.random.randn(5, 1)
print(b)

print(b.T)
```

```python
print(np.dot(b, b.T))
```


