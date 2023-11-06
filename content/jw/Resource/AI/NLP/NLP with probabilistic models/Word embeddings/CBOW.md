---
tags:
  - AI/NLP/Word-Embedding
---

(Google, 2013)

To create word [[Embedding]]s, you need a corpus and a learning algorithm.
The by-product of this task would be a set of word embeddings.

>[!CBOW Objective]
>Predict a missing word based on the surrounding words.

![[Screenshot 2023-09-08 at 2.40.20 AM.png]]

![[Pasted image 20230906033452.png]]

## How CBOW works

![[Pasted image 20230906033521.png]]

## CBOW overview

![[Pasted image 20230906033611.png]]


## Architecture for the CBOW model

![[Pasted image 20230906040453.png]]

$$
\begin{align}
& z_{1} = W_{1}x + b_{1} \\
& h = \text{ReLU}(z_{1}) \\
& z_{2} = W_{2}h + b_{2} \\
& \hat{y} = \text{softmax}(z_{2})
\end{align}
$$

## Training CBOW model
#### CBOW Cost function

$$
J = - \sum^{V}_{k=1} y_{k} \log \hat{y}_{k}
$$
![[Pasted image 20230906040739.png]]

#### CBOW forward propagation
$$
​\begin{align}
& Z_{1} = W_{1}X + B_{1}  \\
& H = \text{ReLU}(Z_{1}) \\
& Z_{2} = W_{2}H + B_{2}  \\
& \hat{Y} = \text{softmax}(Z_{2})
\end{align}
$$

![[Pasted image 20230906041005.png]]

$$
\begin{align}
J_{\text{batch}} = - \frac{1}{m} \sum^{m}_{i=1}\sum^{V}_{j=1} y^{(i)}_{j} \log \hat{y}^{(i)}_{j}
\end{align}
$$

![[Pasted image 20230906041129.png]]

#### CBOW backpropagation and gradient descent
$$
\begin{align}
& \frac{{\partial J_{\text{batch}}}}{\partial W_{1}} = \frac{1}{m} (W^{T}_{2}(\hat{Y} - Y) \cdot step(Z_{1}))X^{T}  \\
& \frac{{\partial J_{\text{batch}}}}{\partial W_{2}} = \frac{1}{m} (\hat{Y} - Y)H^{T}\\
& \frac{{\partial J_{\text{batch}}}}{\partial b_{1}} = \frac{1}{m}(W_{2}^{T}(\hat{Y} - Y) \cdot step(Z_{1}))1^{T}_{m}\\
& \frac{{\partial J_{\text{batch}}}}{\partial b_{2}} = \frac{1}{m}(\hat{Y}-Y)1^{T}_{m}
\end{align}
$$

$$
\begin{align}
& W_{1} := W_{1} - \alpha  \frac{{\partial J_{\text{batch}}}}{\partial W_{1}}  \\
& W_{2} := W_{2} - \alpha  \frac{{\partial J_{\text{batch}}}}{\partial W_{2}}  \\
& b_{1} := b_{1} - \alpha  \frac{{\partial J_{\text{batch}}}}{\partial b_{1}}  \\
& b_{2} := b_{2} - \alpha  \frac{{\partial J_{\text{batch}}}}{\partial b_{2}}  \\

\end{align}
$$



## Extracting word embedding vectors

#### Option 1
![[Pasted image 20230906041736.png]]

#### Option 2
![[Pasted image 20230906041746.png]]

#### Option 3
![[Pasted image 20230906041758.png]]

