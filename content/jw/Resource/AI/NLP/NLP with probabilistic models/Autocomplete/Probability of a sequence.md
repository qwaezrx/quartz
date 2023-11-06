---
tags:
  - AI/NLP
---

$$
\begin{align}
& P(B \mid A) = \frac{P(A, B)}{P(A)} \implies P(A, B) = P(A)P(B\mid A)  \\
& P(A, B, C, D) = P(A)P(B|A)P(C|A, B)P(D|A, B, C)
\end{align}
$$


#### Approximation of sequence probability
Corpus = the teacher drinks tea
$$
P(\text{tea}\mid \text{the teacher drinks}) \approx P(\text{tea} \mid \text{drinks})
$$

- Markov assumption: only last N words matter

- __Bigram__: $$P(w_{n}|w^{n-1}_{1}) \approx P(w_{n}|w_{n-1})$$
- __[[N-Grams]]__: $$P(w_{n}|w^{n-1}_{1}) \approx P(w_{n}| w^{n-1}_{n-N+1})$$ 
- __Entire sentence__:$$
\begin{align}
& P(w^{n}_{1}) \approx P(w_{1})P(w_{2}|w_{1})P(w_{3}|w_{2})\dots P(w_{n}|w_{n-1}) \\
& P(w^{n}_{1}) \approx \prod^{n}_{i=1}P(w_{i}|w_{i-1})
\end{align}
$$

