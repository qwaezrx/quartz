---
tags:
  - AI/NLP/Word-Embedding
---

## Global vectors for word representation

- Not used very much as the [[Word2Vec]] or the [[Skip-gram]] models
- Very simple

$$
\begin{align}
& c, t \\
& x_{ij} = \text{n times i (t) appears in context of j (c)}
\end{align}
$$

## Model 
Minimize $\sum^{10000}_{i=1}\sum^{10000}_{j=1}f(X_{ij})(\theta^{T}_{i}e_{j}+ b_{i} + b_{j}' - \log X_{ij})^{2}$
$X_{ij} = 0 \implies f(X_{ij}) = 0$
$\theta_{i}, e_{j}$ are symmatric 


## See More
- [GloVe: Global Vectors for Word Representation](https://nlp.stanford.edu/projects/glove/) (Pennington, Socher & Manning, 2014)