---
tags:
  - AI/Training
---


Regularization is a method to prevent the high [[Bias & Variance#High variance]] problem and [[Overfitting]].


## [[Logistic regression#Regularization]]

## [[Neural Network]]
$$
\begin{align}
& J(w^{[1]}, b^{[1]}, \dots , w^{[L]}, b^{[L]}) = \frac{1}{m} \sum^{m}_{i=1} Loss(\hat{y}^{(i)}, y^{(i)}) + \frac{\lambda}{2m}\sum^{L}_{l=1}\|w^{[l]}\|^{2}_{F} \\ \\

 & \text{Frobinious norm}\\
& \|w^{[l]}\|^{2}_{F} = \sum^{n^{[l]}}_{i=1}\sum^{n^{[l-1]}}_{j=1}(w^{[l]}_{ij})^{2}

\end{align}
$$
### [[Gradient descent]]
$$
\begin{align}
& dW^{[l]} = \text{(from backprop)} + \frac{\lambda}{m}W^{[l]} \\
& \to W^{[l]}:= W^{[l]} - \alpha dW^{[l]}
\end{align}
$$

## [[Dropout]]

## [[Data augmentation]]

## Early stopping

