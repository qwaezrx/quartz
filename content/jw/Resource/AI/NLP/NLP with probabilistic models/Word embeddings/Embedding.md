---
tags:
  - AI/NLP/Word-Embedding
---

## Introduction

>Process of representing words or phrases as high-dimensional [[Vector]]s in continuous space, such that similar words are mapped to nearby points in that space

$$
f(x) \in \mathbb{R}^{d}
$$
- d-차원의 [[Euclidean Space]]에 $x$ 를 임베딩
## Word embeddings usage

![[Pasted image 20230906030845.png]]

![[Pasted image 20230906030849.png]]

## Benefits of word embeddings
- Low dimensions (less than V)
- Allow you to encode meaning


## Word embedding method

![[Screenshot 2023-09-06 at 3.21.59 AM.png]]

#### [[Self-supervised learning]]
= unsupervised + supervised
#### Hyperparameters
Word embeddings can be tuned by a number of hyperparameters just like in any [[Model(AI)]]

- Word embedding size (dimension)
	- typically (100s ~ 1000s)
	- higher dimensions => higher computation

#### Pre-transformation
Words -> integers, one-hot vectors




