---
tags:
  - AI/NLP
---

$$
\begin{align}
& PE_{(pos, 2i)} = \sin\left( \frac{pos}{10000^{2i/d}} \right) \\
& PE_{(pos, 2i+1)} = \cos\left( \frac{pos}{10000^{2i/d}} \right)
\end{align}
$$
- $d$ : dimension of the word embedding and positional encoding
- $pos$ : position of the word
- $k$: each of the different dimensions in the positional encoding
- $i = k // 2$

## Sine and Cosine angles
$$
\theta(pos, i, d) = \frac{pos}{10000^{2i/d}}
$$

