---
tags:
  - AI/CV
---


## Motivation for MobileNets
- Low computational cost at deployment
- Useful for mobile and embedded vision applications
- Key idea: Normal vs. depthwise-separable convolutions

## Normal Convolution vs. MobileNet
#### Normal Convolution
Computational cost = filter params * filter positions * n_filters
- = (f * f * n_C) * ((n_H - f + 1) * (n_W - f + 1)) * n_filters
#### Depthwise Separable Convolution
__Depthwise Convolution__
Computational cost = filter params * filter positions * n_filters
- = (f * f) * ((n_H - f + 1) * (n_W - f + 1)) * n_C

__Pointwise Convolution__
(n_out, n_out, n_C) * (1, 1, n_C) = (n_out, n_out, n_filters)
Computational cost = filter_params * filter posiitons * n_filters
- = (n_C) * ((n_H - f + 1) * (n_W - f + 1)) * n_filters
#### Equation
$$
\begin{align}
& 
\frac{\text{DS conv cost}}{\text{Normal conv cost}} = \frac{1}{n_{C}'} + \frac{1}{f^{2}}  \\ \\

& (n_{C}' = 512, f = 3) \implies 
\frac{\text{DS conv cost}}{\text{Normal conv cost}} \approx \frac{1}{10}
\end{align}
$$


![[IMG_EECA6219AFF8-1.jpeg]]

[[ResNet]]

![[IMG_D48448805A1E-1.jpeg]]


