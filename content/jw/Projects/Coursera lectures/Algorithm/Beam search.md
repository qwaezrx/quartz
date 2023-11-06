---
tags:
  - CS/Algorithm
---


![[IMG_8564ADDB2899-1.jpeg]]

With a beam of 3 being searched considers 3 possibilities at a time.

- If B = 1, [[Greedy search]]

## Refinements to beam search
#### Length normalization
$$
\begin{align}
arg\max_{y} \prod^{T_{y}}_{t=1} P(y^{<t>} \mid x, y^{<1>}, \dots, y^{<t-1>})  \\
arg \max_{y}\sum^{T_{y}}_{y=1} \log P(y^{<t>} | x, y^{<1>}, \dots , y^{<t-1>}) \\
\to \frac{1}{T_{y}^{\alpha}} arg \max_{y}\sum^{T_{y}}_{y=1} \log P(y^{<t>} | x, y^{<1>}, \dots , y^{<t-1>})  \\ \\
(\alpha = 0) \implies \text{No normalization}

\end{align}
$$

## Beam search discussion
How to choose B?
- large B: better result, slower
- small B: worse result, faster

usually 1~ 10, possible 100 (very large)

unlike exact search algorithms like [[BFS]] or [[DFS]], beam search runs faster but is not guaranteed to find exact maximum for $arg\max_{y}P(y\mid x)$.

## Error analysis on beam search
Case 1:
Beam search chose $\hat{y}$ but $y^{*}$ attains higher $P(y\mid x)$.
Conclusion: Beam search is at fault

Case 2:
$y^{*}$ is a better translation than $y^{*}$ but RNN predicted $P(y^{*}\mid x) \leq P(\hat{y}\mid x)$
Conclusion: RNN model is at fault

![[IMG_F3BDE3E29F9A-1.jpeg]]




