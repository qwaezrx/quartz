---
tags:
  - AI
---

$$
X = \frac{{X-\mu}}{\sigma}
$$
- Normalizing inputs can speed up learning
- You can normalize $A$ to train $W, b$ faster
- Normalizing $Z$ is used much more often

- Has very slight [[Regularization]] effect too (don't use for regularization though)

>[!note]
>The regularization effect reduces when mini-batch size increases

## Implementing batch norm

$$
\begin{align}
& \text{Given some intermediate values in NN } Z^{(1)}, Z^{(2)},\dots, Z^{(m)}  \\
& \mu = \frac{1}{m} \sum^{m}_{i=1} Z^{(i)} \\
& \sigma^{2} = \frac{1}{m} \sum^{m}_{i=1} (Z^{(i)} - \mu)^{2}  \\
& Z^{(i)}_{\text{norm}} = \frac{Z^{(i)} - \mu}{\sqrt{ \sigma^{2} + \epsilon }}  \\ \\

& \tilde{Z}^{(i)} = \gamma Z^{(i)}_{\text{norm}} + \beta  \\
& \gamma, \beta : \text{Learnable parameters}
\end{align}
$$

if $\gamma = \sqrt{ \sigma^{2} + \epsilon }$ and $\beta = \mu$ -> $\tilde{Z}^{(i)} = Z^{(i)}_{\text{norm}}$

## Adding batch norm to a [[Neural Network]]

$$
X =W^{[1]}, b^{[1]} \implies Z^{[1]} = \gamma, \beta (\text{Batch Norm}) \implies  \tilde{Z}^{[1]} \implies A^{[1]} = g(\tilde{Z}^{[1]})
$$

>[!important]
>When implementing Batch Norm, parameter $b$ will be useless


## Why does batch-norm works?
Batch norm makes weights, later or deeper than your network, like layer 10, more robust to changes to weights in earlier layers of the neural network like in layer 1.

[[Covariate shift]] problem: if you learned some X to Y mapping, if the distribution of X changes, then you might need to retain your learning algorithm.

So the batch norm reduces the amount that the distribution of these hidden unit values shifts around.