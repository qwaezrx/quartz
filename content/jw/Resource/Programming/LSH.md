---
aliases:
  - Locality Sensitive Hashing
  - locality sensitive hashing
---

## Locality Sensitive Hashing
Method to reduce the computational cost of finding neighbors in high dimensional spaces.

LSH allows you to hash similar inputs into the same buckets with high probability.


Given some points
vector with point P is perpendicular to the _plane_
$$
\begin{align}
& \mathbf{P} = \begin{pmatrix}
1 & 1
\end{pmatrix} \\
& \mathbf{V}_{1} = \begin{pmatrix}
1 & 2
\end{pmatrix}\\
& \mathbf{V}_{2}= \begin{pmatrix}
-1 & 1
\end{pmatrix}\\
& \mathbf{V}_{3} = \begin{pmatrix}
-2 & -1
\end{pmatrix}
\end{align}
$$
Get the dot product value for each V:
$$
\begin{align}
& \mathbf{PV}^{T}_{1} = 3 \\
& \mathbf{PV}^{T}_{2} = 0 \\
& \mathbf{PV}^{T}_{3} = -3
\end{align}
$$

if the value is 0, then it is on the plane and different signs means each points are on different side of the plane.

### Single plane In Python
```python
def side_of_plane(P, v):
	dotproduct = np.dot(P, v.T)
	sign_of_dot_product = np.sign(dotproduct)
	sign_of_dot_product_scalar = np.asscaler(sign_of_dot_product)
	return sign_of_dot_product_scalar
	
```

# Multiple planes
- Multiple planes -> Dot products -> Hash values
$$
\begin{align}
& \mathbf{P}_{1}\mathbf{v}^{T} = 3, sign_{1} = +1, h_{1} = 1  \\
& \mathbf{P}_{2}\mathbf{v}^{T} = 5, sign_{1} = +1, h_{1} = 1  \\
& \mathbf{P}_{3}\mathbf{v}^{T} = -2, sign_{1} = -1, h_{1} = 0  \\ \\
& hash = 2^{0} \times h_{1} + 2^{1} \times h_{2} + 2^{2} \times h_{3}  \\
& = 1 \times 1 + 2 \times 1 + 4 \times 0 \\
& = 3 \\
\\
& sign_{i} \geq 0, \to h_{i} = 1  \\
& sign_{i} < 0, \to h_{i} = 0 \\
& \text{hash} = \sum^{H}_{i} 2^{i} \times h_{i}
\end{align}
$$

![[Pasted image 20230908202503.png]]


### Multiple planes, single hash value, Python

```python
def hash_multiple_plane(P_l, v):
	hash_value = 0
	for i, P in enumerate(P_l):
		sign = side_of_plane(P, v)
		hash_i = 1 if sign >= 0 else 0
		hash_value += (2 ** i) * hash_i

	return hash_value
```

