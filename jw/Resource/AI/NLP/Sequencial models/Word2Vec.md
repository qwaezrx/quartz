---
tags:
  - AI/NLP/Word-Embedding
---


## Model
- Vocab size = 10000
	- Some have been on vocab sizes that exceeds a million words

The basic supervised learning problem we're going to solve is that we want to learn the mapping from some context c (such as a word "orange") to some target y ("juice")

$x (\text{"orange", 6257}) \to y(\text{"juice", 4834})$

$$
\begin{align}
\mathbf{o}_{c} \to \mathbf{E} \to \mathbf{e}_{c} \to (\text{softmax}) \to \hat{y} \\
& o_{c}: \text{One hot vector (context)} \\
& \mathbf{E}: \text{Embedding matrix}  \\
& \mathbf{e}_{c} = \mathbf{E} \cdot \mathbf{o}_{c} \\
& t: \text{target} \\
& c: \text{context} \\
& \text{softmax}: P(t\mid c) = \frac{e^{\theta^{T}_{t}e_{c}}}{\sum^{10000}_{j=1}e^{\theta^{T}_{j}e_{c}}} \\
& \theta_{t}: \text{parameter associated with output }t
\end{align}
$$

- The matrix E will have a lot of parameters
- The softmax unit also have $\theta_{t}$ parameters

Trying to predict some words skipping a few words from the left or the right side to predict what comes little bit before or little bit after the context words.

## Problems with softmax classification
$$
p(t\mid c) = \frac{e^{\theta^{T}_{t}e_{c}}}{\sum^{10000}_{j=1}e^{\theta^{T}_{j}e_{c}}}
$$
- Computational speed
	- Every time, you need to carry out a sum over all 10000 (or more) words in your vocab
	- Solution:
		- Hierarchical softmax classifier
			- cost Big O (log|vocabs|)

How to sample the context c?

## Skip-gram
## Cbow



