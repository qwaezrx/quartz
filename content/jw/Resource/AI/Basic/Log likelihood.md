---
tags:
  - AI
---

Prev: [[Naive Bayes]]

Log likelihoods are just logarithms of the probabilities. They are way more convenient to work with and they appeared throughout deep learning and NLP. Let's go back to the table you saw previously that contains the conditional probabilities of each word. For positive or negative sentiment. Words can have many shades of emotional meaning, but for the purpose of sentiment classification, they're simplified into three categories;

## Ratio of probabilities
| word  | Pos  | Neg | ratio |
| ----- | ---- | --- | ----- |
| I     | 0.2  | 0.2 | 1     |
| am    | 0.2  | 0.2 | 1     |
| happy | 0.15 | 0.1 | 1.5   |
$$
ratio(w_{i}) = \frac{P(w_{i}|\text{Pos})}{P(w_{i}|\text{Neg})}
$$

## Naive Bayes' inference
$$
\begin{aligned}
& \text{class} \in \{ \text{pos}, \text{neg} \} \\
& w \to \text{Set of words in a sentence} \\ \\
& \text{Prior ratio} \to \frac{P(pos)}{P(neg)}\\ \\
& \text{Likelihood} \to\prod_{i=1}^{m} \frac{P(w_{i}|pos)}{P(w_{i}|neg)} > 1 \\ \\
& \text{ratio applied} \to \frac{P(pos)}{P(neg)} \prod^{m}_{i=1} \frac{P(w_{i}|pos)}{P(w_{i}|neg)} > 1
\end{aligned}
$$

- A simple, and powerful baseline
- A probabilistic model used for [[Classification]].

