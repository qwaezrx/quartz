[[NumPy]]
# General principle
$$
\begin{align}
& (m, n) \pm (1, n) \to (m, n) \\
& (m, n) \pm (m, 1) \to (m, n) 
\end{align}
$$

## [[NumPy]] example
```python
import numpy as np

A = np.array([[1, 2, 3, 4],
			 [5, 6, 7, 8],
			 [9, 3, 2, 5]])

cal = A.sum(axis=0)
print(cal)
print(f"cal shape: {cal.shape}")

percentage = 100 * A / (cal.reshape(1, 4))
print(percentage)
percentage = 100 * A / cal
print(percentage)

```

