#AI 


[[Cost function]]
[[Loss function]]

The general form of gradient descent is defined as:

Repeat {
	$\theta := \theta_j - \alpha\dfrac{\delta}{\delta\theta_j}J(\theta)$
}

$J = \text{Cost function}$

When dealing with $J(w, b)$:
Repeat {
	$w:= w - \alpha  \frac{\delta}{\delta w}J(w, b)$
	$b:= b - \alpha  \frac{\delta}{\delta b}J(w, b)$
}

# Gradient descent for [[Neural Network]]s
__Parameters__: $W^{[1]}, b^{[1]}, W^{[2]}, b^{[2]}$
- $W^{[1]} = \mathbb{R}^{n^{[1]} \times n^{[0]}}$
- $b^{[1]} = \mathbb{R}^{n^{[1]} \times 1}$
- $W^{[2]} = \mathbb{R}^{n^{[2]} \times n^{[1]}}$
- $b^{[1]} = \mathbb{R}^{n^{[2]} \times 1}$
- $n_{x} = n^{[0]}$
- $n^{[2]} = 1$
__Cost function__: $$J(W^{[1]}, b^{[1]}, W^{[2]}, b^{[2]}) = \frac{1}{m}\sum^{m}_{i=1} h(\hat{y}, y)$$
__Gradient descent__:
Repeat {
	Compute predicts $(\hat{y}^{(i)}, i=1\dots m)$
	$dW^{[1]} = \frac{dJ}{dW^{[1]}}, db^{[1]} = \frac{dJ}{db^{[1]}}, \dots$
	$W^{[1]} = W^{[1]} - \alpha dW^{[1]}$
	$b^{[1]} = b^{[1]} - \alpha db^{[1]}$
	$W^{[2]} = W^{[2]} - \alpha dW^{[2]}$
	$b^{[2]} = b^{[2]} - \alpha db^{[2]}$
}

## Formulas for computing derivatives
### Forward propagation:
$$
\begin{align}
& Z^{[1]} = W^{[1]}X + b^{[1]} \\
& A^{[1]} = g^{[1]}(Z^{[1]})  \\
& Z^{[2]} = W^{[2]}A^{[1]} + b^{[2]} \\
& A^{[2]} = g^{[2]}(Z^{[2]}) = \sigma(Z^{[2]})
\end{align}
$$
### Back propagation:
$$
\begin{align}
& dZ^{[2]} = A^{[2]} - Y  \\
& dW^{[2]} = \frac{1}{m} dZ^{[2]} A^{[1]T}  \\
& db^{[2]} = \frac{1}{m} \sum dZ^{[2]} \\
& dZ^{[1]} = \underset{n^{[1]} \times m}{W^{[2]T}dZ^{[2]}} * \underset{n^{[1]} \times m}{g^{[1]} {'} (Z^{[1]})} \\
& dW^{[1]} = \frac{1}{m}dZ^{[1]}X^{T}  \\
& db^{[1]} = \frac{1}{m} \sum dZ^{[1]}
\end{align}
$$
__In python code__:
```python

db_2 = 1/m * np.sum(dZ_2, axis=1, keepdims=True)

db_1 = 1/m * np.sum(dZ_1, axis=1, keepdims=True)
```


## See more
- [https://blog.paperspace.com/intro-to-optimization-in-deep-learning-gradient-descent/](https://blog.paperspace.com/intro-to-optimization-in-deep-learning-gradient-descent/)

