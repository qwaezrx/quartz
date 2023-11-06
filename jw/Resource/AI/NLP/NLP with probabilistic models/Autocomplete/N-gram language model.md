---
tags:
  - AI/NLP
---

[[N-Grams]]

## Count matrix
- __Rows__: unique corpus (N-1)-grams
- __Columns__: unique corpus words

![[Screenshot 2023-09-05 at 9.57.56 PM.png]]

$$
C(w^{n-1}_{n-N+1}, w_{n})
$$

## Probability matrix
- Divide each cell by its row sum

$$
sum(row) = \sum_{w \in V}C(w^{n-1}_{n-N+1}, w) = C(w^{n-1}_{n-N+1})
$$
![[Screenshot 2023-09-05 at 10.03.19 PM.png]]

$$
\begin{align}
P(w_{n}\mid w_{n-N+1}^{n-1}) = \frac{{C(w_{n-N+1}^{n-1}, w_{n})}}{C(w^{n-1}_{n-N+1})}
\end{align}
$$

## Language model
- Probability matrix => language model
	- Sentence probability


## Log probability
- All probabilities in calculation <= 1 and multiplying them brings risk of underflow

$$
P(w^{n}_{1}) \approx \prod^{n}_{i=1} P(w_{i} \mid w_{i-1})
$$
$$
\log(P(w^{n}_{1})) \approx \sum^{n}_{i=1}\log(P(w_{i}\mid w_{i-1}))
$$


## Generative language model
Algorithm:
1. Choose sentence start
2. Choose next bigram starting with previous word
3. Continue until \</s> is picked


