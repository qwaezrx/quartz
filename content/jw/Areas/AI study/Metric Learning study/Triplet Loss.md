---
tags:
  - AI/Loss_Function
---


## Introduction

_Triplet Loss_ 는 baseline 인 anchor를 positive, negative input들과 비교하는 Loss Function이다.

목적: anchor input과 positive input 사이의 거리는 최소화, negative input과의 거리는 최대화시키는 것.

compare pairs of images, texts, etc.

## Triplet Loss
__Images__
have to look at several pictures at the same time
![[Screenshot 2023-09-05 at 12.01.18 AM.png]]

__Texts__
![[Pasted image 20230906204118.png]]

![[Pasted image 20230906204301.png]]


A = Anchor input
P = Positive input
N = Negative input

Want = $\mid\mid f(A) - f(P) \mid\mid^{2} + \alpha \leq \mid\mid f(A) - f(N)\mid\mid^{2}$
$= d(A, P) \leq d(A, N)$

$\mid\mid f(A) - f(P) \mid\mid^{2} -  \mid\mid f(A) - f(N)\mid\mid^{2} + \alpha \leq 0$


## Loss function
Given 3 images A, P, N 
$$
\begin{align} 
& \mathcal{L}(A, P, N) =  max(\begin{Vmatrix}
f(A) - f(P)
\end{Vmatrix}^{2} - \begin{Vmatrix}
f(A) - f(N)
\end{Vmatrix}^{2} + \alpha, 0) \\
& \mathcal{J} = \sum^{m}_{i=1}\mathcal{L}(A^{(i)}, {P^{(i)}}, N^{{i}})
\end{align}
$$

Training set: 10k pictures of 1k persons


![[Screenshot 2023-09-06 at 8.49.45 PM.png]]


## Choosing the triplets A, P, N
During training, if A, P, N are chosen randomly,
$d(A, P) + \alpha \leq d(A, N)$ is easily satisfied.

Choose triplets that're "hard" to train on.

![[Screenshot 2023-09-06 at 8.52.25 PM.png]]

####  Triplet loss; Computing cost 1

![[Pasted image 20230906205447.png]]

![[Pasted image 20230906205451.png]]

####  Triplet loss; Computing cost 2

![[Pasted image 20230906205915.png]]

![[Screenshot 2023-09-06 at 8.59.52 PM.png]]

## Triplet loss summary
- $\alpha$: controls how far $cos(A, P)$ is from $cos(A, N)$
- __Easy__ negative triplet: $\cos(A, N) < \cos(A, P)$
- __Semi-hard__ negative triplet: $\cos(A, N) < \cos(A, P) < \cos(A, N) + \alpha$
- __Hard__ negative triplet: $\cos(A, P) < \cos(A, N)$


