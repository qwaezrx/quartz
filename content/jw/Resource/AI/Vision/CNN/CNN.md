---
tags:
  - AI/CV
aliases:
  - Convolutional Neural Network
---

$$
\begin{align}
\underset{ n \times n }{ \begin{pmatrix}
3 & 0 & 1 & 2 & 8 & 6 \\
9 & 7 & 5 & 7 & 3 & 8 \\
9 & 7 & 5 & 7 & 9 & 6 \\
0 & 9 & 1 & 3 & 6 & 3 \\
9 & 8 & 6 & 9 & 0 & 8
\end{pmatrix} } * \underset{ f \times f }{ \begin{pmatrix}
w_{1} & w_{2} & w_{3} \\
w_{4} & w_{5} & w_{6}  \\
w_{7} & w_{8} & w_{9}
\end{pmatrix} } = \mathbb{R^{(n-f+1) \times (n-f+1)}}
\end{align}
$$

## Introduction

>A type of [[Neural Network]] that works particularly well for [[Computer vision]] tasks.

## Why convolutions
### __Parameter sharing:__ 
A feature detector (such as a vertical edge detector) that's useful in one part of the image is probably useful in another part of the image.

### __Sparsity of connections:__
In each layer, each output value depends only on a small number of inputs


# Types of layers in convolutional network
- [[#Convolutional layer]] (Conv)
- [[#Pooling layer]]
- Pooling layer (Pool)
- Fully connected layer (FC)


# CNN Backpropagation

## CNN dA:
$$
\begin{align}

& dA += \sum^{n_{H}}_{h = 0}\sum^{n_{W}}_{w=0}W_{c} * dZ_{hw} \\ \\
& W_{c}: \text{filter}  \\
& dZ_{hw}: \text{scalar corresponding to the gradient of the cost} \\
&\text{with respect to the output of the conv layer Z}   \\ \\
& dW += \sum^{n_{H}}_{h=0}\sum^{n_{W}}_{w=0}a_{\text{slice}} * dZ_{hw} \\
& db += \sum^{n_{H}}_{h=0}\sum^{n_{W}}_{w=0}dZ_{hw} \\

\end{align}
$$


## See more
https://www.coursera.org/learn/convolutional-neural-networks/programming/4xt9A/convolutional-model-step-by-step