---
tags:
  - AI
---


- Q = interesting questions about the words in a sentence
- K = qualities of words given a Q
- V = specific representations of words given a Q

$A(q, K, V)$ = attention-based vector representation of a word
-> Calculate for each word $A^{<1>}, A^{<2>}, \dots$

$$
A(q, K, V) = \sum_{i} \frac{{\exp(q \cdot k^{<i>})}}{\sum_{j}\exp(q \cdot k^{<j>})}v^{<i>}
$$

$$
\begin{align}

& q^{<t>} = W^{Q} x^{<t>} \\
& K^{<t>} = W^{K} x^{<t>}  \\
& V^{<t>} = W^{V} x^{<t>}
\end{align}
$$


$$
Attention(Q, K, V) = \text{softmax}\left( \frac{{QK^{T}}}{\sqrt{ d_{k} }} \right)V
$$



