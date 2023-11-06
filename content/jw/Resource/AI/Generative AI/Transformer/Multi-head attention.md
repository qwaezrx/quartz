---
tags:
  - AI/Transformer
---

[[Attention model]] with $h$ heads

$$
\begin{align}
Attention(W^{Q}_{h}Q, W^{K}_{h}K, W^{V}_{h}V)
\end{align}
$$


![[Screenshot 2023-09-04 at 5.35.26 PM.png]]


$$
\begin{align}
& Multihead(Q, K, V) = concat(head_{1}, head_{2}, \dots, head_{h})W^{O}  \\
& head_{i} = Attention(W^{Q}_{i}, W^{K}_{i}K, W^{V}_{i}V)
\end{align}
$$


>[!note]
>In the simplest case of self multi-headed attention you would actually use $q=k=v=x$

