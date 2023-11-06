
[[Neural Network]]
[[NumPy]]
# NN programming guideline
## Whenever possible, avoid explicit for-loops.
### Example
If you need to apply the exponential operation on every element of a matrix/vector.

__Bad__
```python
import numpy as np
import math

v = np.array([3, 3, 6, 32, 5, 6, 7, 3])
n = len(v)
u = np.zeros((n))
for i in range(n):
	u[i] = math.exp(v[i])

print(u)
```

__Good__
```python
import numpy as np

v = np.array([3, 3, 6, 32, 5, 6, 7, 3])
u = np.exp(v)

print(u)
```

__Other functions__
```python
import numpy as np

v = np.array([3, 3, 6, 32, 5, 6, 7, 3])

print(np.log(v))
print(np.abs(v))
print(np.maximum(v, 10))
print(v ** 2)
```

# Examples
## Vectorizing Logistic Regression
Without vectorizing:
$$
\begin{align} \\
& \text{for i in (1...m):} \\
& \quad z^{(i)} = \vec{w}^{T}\vec{x}^{(i)} + b
\end{align}
$$
with vectorizing:
$$
\begin{align}
& \mathbf{X} = \begin{bmatrix}
\vert & \vert &  & \vert \\
x^{(1)} & x^{(2)} & \dots  & x^{(m)} \\
\vert & \vert &  & \vert
\end{bmatrix} = \mathbb{R}^{n_x \times m} \\ 
& \mathbf{w} = \mathbb{R}^{n_{x} \times 1} \\
& b = \mathbb{R}^{1\times 1} \\
& \mathbf{z} = \mathbf{w}^{\mathbf{T}}\mathbf{X} + b = \mathbb{R}^{1\times m} \\

& \mathbf{a} = \sigma(\mathbf{z})
\end{align}
$$
### In python
```python
# X shape(n_x, m)
# w shape(n_x, 1)
z = np.dot(w.T, X) + b # shape(1, m)
a = sigmoid(z) # shape(1, m)

dz = a - y # shape(1, m)
db = 1/m * np.sum(dz)
dw = 1/m * np.dot(X, dz.T) # shape(n_x, 1)
```
