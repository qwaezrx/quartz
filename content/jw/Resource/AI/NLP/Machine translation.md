---
tags:
  - AI/NLP
---

# Transforming word vectors

## NumPy example
```python
R = np.array([[2, 0],
			  [0, -2]])

x = np.array([[1, 1]])

np.dot(x, R)
# arrauy([[2, -2]])
```

## Align word vectors
$$
\mathbf{XR} \approx \mathbf{Y}
$$
We can start with randomly selected $\mathbf{R}$ and see how it performs when you try to translate the English vectors in matrix $\mathbf{X}$ and compare that to the actual french word vectors which is in the matrix $\mathbf{Y}$ 

$$
\mathbf{X} = \begin{pmatrix}
[\text{"cat" vector}] \\
\vdots \\
[\text{...vector}]
\end{pmatrix}
\;\;
\mathbf{Y} = \begin{pmatrix}
[\text{"chat" vecteur}] \\
\vdots \\
[\text{...vecteur}]
\end{pmatrix}
$$

## Solving for R
1. initialize R
2. in a loop:
	- Get loss using [[Frobenius norm]].
	- When calculating $g$, you pretend that $\mathbf{R}$ as a single variable instead of a matrix.
$$
\begin{align}
& Loss = \lVert \mathbf{XR-Y} \rVert_{F}^{2} \\
& g = \frac{d}{dR}Loss = \frac{2}{m}(\mathbf{X}^T(\mathbf{XR-Y})) \\
& R = R - \alpha g
\end{align}
$$


