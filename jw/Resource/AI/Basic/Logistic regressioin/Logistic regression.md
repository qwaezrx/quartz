---
tags:
  - AI/Logistic_Regression
---

>[!note]
>Logistic regression is a 1-layer [[Neural Network]]


$$\begin{align} \\
& \sigma(z) = \frac{1}{1 + e^{-z}} \\

& h(x^{(i)}, \theta) = \sigma(\theta^T x^{(i)}) = \dfrac{1}{1 + e^{-\theta^T x^{(i)}}}
\end{align}$$

## Types of logistic regression
Logistic regression includes three basic types:
### Binary
A binary output is a variable where there is only two possible outcomes. These outcomes must be opposite of each other and mutually exclusive. Whether you get a job or not is a binary output.

$$
\begin{align}
& \text{Given } x, \text{want } \hat{y} = P(y=1|x) \\
& x \in \mathbb{R}^{n_{x}}  \\
& \text{Parameters}: w \in \mathbb{R}^{n_{x}}, b \in \mathbb{R} \\
& \text{Output } \hat{y} = \sigma{(w^{T}x + b)} \\
\\
& \sigma(z) = \frac{1}{1 + e^{-z}}
 \end{align}
$$
### Multi-class
A multi-class has three or more categories without any numerical value, though they usually have a numerical stand-in for datasets. For example, you could ask if someone of they have a dog, cat or fish.
### Ordinal
An ordinal output also has three or more categories, though they're in a ranked output. For example, asking for a movie rank from 0 to 5 is an ordinary output.

## Multivariable vs. multivariate logistic regression
There is only one key difference between them.
### Multivariable regression
Has multiple independent variables and multiple outcomes.
### Multivariate regression
Has multiple independent variables but only one outcome.

## Partial derivative
$$
\begin{gathered}
\frac{\delta}{\delta\theta_{j}}J(\theta) = \frac{\delta}{\delta\theta_{j}}\frac{-1}{m}\sum_{i=1}^m[y^{(i)}\log(h(x^{(i)}, \theta)) + (1-y^{(i)})\log(1-h(x^{(i)}, \theta))]
\\
= -\frac{1}{m}\sum_{i=1}^m\left[ y^{(i)} \frac{\delta}{\delta\theta_{j}}\log(h(x^{(i)}, \theta)) + (1-y^{(i)}) \frac{\delta}{\delta\theta_{j}}\log(1-h(x^{(i)}, \theta)) \right]\\
= - \frac{{1}}{m}\sum_{i=1}^{m}\left[ \frac{{y^{(i)} \frac{\delta}{\delta\theta_{j}}h(x^{(i)}, \theta)}}{h(x^{(i)}, \theta)} + \frac{{(1-y^{(i)}) \frac{\delta}{\delta\theta_{j}}(1-h(x^{(i)}, \theta))}}{1-h(x^{(i)}, \theta)} \right] \\
= -\frac{{1}}{m} \sum_{i=1}^m \left[ \frac{{y^{(i)} h(x^{(i)}, \theta)(1-h(x^{(i)}, \theta))x^{(i)}_{j}}}{h(x^{(i)}, \theta)} - \frac{{(1 - y^{(i)})h(x^{(i)}, \theta)(1-h(x^{(i)}, \theta))x^{(i)}_{j}}}{1-h(x^{(i)}, \theta)} \right] \\
= - \frac{{1}}{m}\sum^{m}_{i=1}\left[ 
y^{(i)}(1-h(x^{(i)}, \theta)x^{(i)}_{j} - (1-y^{(i)})h(x^{(i)}, \theta)x^{(i)}_{j}
 \right] \\
 = - \frac{{1}}{m}\sum^{m}_{i=1} \left[
 y^{(i)} - h(x^{(i)}, \theta)
 \right]x^{(i)}_{j} \\
 = \frac{1}{m}\sum^{m}_{i=1}\left[ h(x^{(i)}, \theta) - y^{(i)} \right]x^{(i)}_{j}
\end{gathered}
$$

The vectorized version:
$$
\nabla J(\theta) = \frac{1}{m} \cdot X^{T} \cdot (H(X, \theta) - Y)
$$

## Regularization

$$
\begin{align}
& \lambda = \text{regularization parameter}
\end{align}
$$

use "lambd" in python as variable name
### L2 regularization:
$$
\begin{align}

& J(w, b) = \frac{1}{m}\sum^{m}_{i=1} L(\hat{y}^{(i)}, y^{(i)}) + \frac{\lambda}{2m}\|w\|^{2}_{2}  \\
& \|w\|^{2}_{2} = \sum^{n_{x}}_{j=1}w_{j}^{2} = w^{T}w  \\
\end{align}
$$
Adding $\frac{\lambda}{2m}b^{2}$ is usually useless

### L1 regularization:
$$
\begin{align}
& \frac{\lambda}{2m} \sum^{n_{x}}_{i=1} |w| = \frac{\lambda}{2m}\|w\|_{1}
\end{align}
$$