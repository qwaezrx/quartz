---
aliases:
  - perplexity
tags:
  - AI/Metric
---


_Perplexity_ is an important metric used to evaluate language models. 

$$
\begin{align}
& PP(W) = P(s_{1}, s_{2}, s_{3}, \dots s_{m})^{-\frac{1}{m} } \\ \\
& W \to \text{test set containing } m \text{ sentences } s  \\
& s_{i} \to \text{i-th sentence in the test set, each ending with </s>} \\
& m \to \text{number of all words in entire test set } W \text{ including </s>} \\ & \quad \quad \text{but not including <s>}
\end{align}
$$

You can think of perplexity as a measure of the complexity in a sample of texts, like how complex that text is

Perplexity is used to tell us whether a set of sentences look like they were written by humans rather than by a simple program choosing words at random.

- Humans             -> lower perplexity score
- Random choice -> higher perplexity score

>[!note]
>_Perplexity_ is basically the inverse probability of the test set normalized by the number of words in the test set

closely related to _entropy_

- Smaller perplexity => better model

>[!note]
>Good language models have _perplexity scores_ between 60 ~ 20, sometimes even lower for english


## Perplexity for bigram models
$$
\begin{align}
& PP(W) = \sqrt[m]{ \prod^{m}_{i=1} \prod^{|s_{i}|}_{j=1} \frac{1}{P(w^{(i)}_{j} \mid w^{(i)}_{j-1})} }  \\ \\
& w^{(i)}_{j} \to \text{j-th word in i-th sentence} 
\end{align}
$$
- Concatenate all sentences in W
$$
\begin{align}
& PP(W) = \sqrt[m]{ \prod^{m}_{i=1} \frac{1}{P(w_{i}\mid w_{i-1})} }  \\ \\
& w_{i} \to \text{i-th word in test set}
\end{align}
$$

## Log perplexity
$$
\begin{align}
& \log PP(W) = -\frac{1}{m}\sum^{m}_{i=1}\log_{2}(P(w_{i}\mid w_{i-1}))
\end{align}
$$

## Perplexity Examples
![[Screenshot 2023-09-05 at 10.36.16 PM.png]]


