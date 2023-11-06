---
tags:
  - Mathematics/Statistics
---

## Principle Component Analysis
PCA is based on the [[SVD]] of the [[Covariance matrix]] of the original dataset. The [[Eigenvector]]s of such decomposition are used as a rotation matrix


[[Eigenvector]]: Directions of uncorrelated features for your data

[[Eigenvalue]]: Variance of the new features

They are useful because the Eigenvectors of the [[Covariance matrix]] from your data, you give directions of uncorrelated features and the Eigenvalues are the variance of your data sets in each of those new features.

1. Mean normalize data
2. Get [[Covariance matrix]]
3. Perform SVD($\sum$)

---

Dot product to project data 
$$
\begin{align}
X' = XU[:, 0:n] \\ \\

U: \text{eigenvector}
\end{align}
$$
Percentage of retained variance
$$
\begin{align}
\frac{\sum^{1}_{i=0}S_{ii}}{\sum_{j=0}^{d}S_{jj}}
\end{align}
$$
