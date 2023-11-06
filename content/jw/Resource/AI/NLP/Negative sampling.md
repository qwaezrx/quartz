---
tags:
  - AI/NLP
---


Negative sampling allows you to do something similar to the Skip-gram model, but much more efficient.

## Defining a new learning problem
The way to generate the data set is, we'll pick a context word and pick a target word and that is the first row of the table (context, target, label). And then we'll do is for some number of times (k), we're going to take the same context word and then pick random words from the dictionary and label all those to 0.

Input: (context, word)
Output: (lable(1 | 0))

k: (5...20) if small dataset, (2...5) if large dataset

$$
\begin{align}
P(y=1 \mid c, t) = \sigma(\theta^{T}_{c}e_{c})
\end{align}
$$

Instead of 10000 binary classification problems, it will be only (k+1) binary classification problems we have to solve.

This technique is called negative sampling because what you're doing is, you have positive example and then you will go and deliberately generate a bunch of negative samples.