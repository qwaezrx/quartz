
sentence = "I am Happy because i am learning NLP @deeplearning"

Perform [[Preprocessing in NLP logistic regression]]
-> $[happy, learn, nlp]$

[[Vocabulary & Feature extraction]]
-> $[1, 4, 2]$

When you have $m$ sentences your $X$ will become a dimension $(m, 3)$ as follows:

$$X = \begin{bmatrix}
	1 && X_1^{(1)} && X_2^{(1)}\\
	1 && X_1^{(2)} && X_2^{(2)}\\
	... && ... && ... \\
	1 && X_1^{(m)} && X_2^{(m)}\\
	\end{bmatrix}$$

When implementing it with code, it becomes as follow:
```python
freqs = build_freq(sentences, labels) # Build frequency dictionary

m = len(sentences)

X = np.zeros((m, 3))

for i, sentence in enumerate(sentences):
	tokens = preprocess(sentence)
	X[i, :] = extract_feature(tokens, freqs)
	
```


Perform [[Logistic regression]]:
- assuming that you have optimal set of parameters $\theta$.
$$x^{(i)} = 
\begin{bmatrix} 
1 \\
4 \\
2 \\
\end{bmatrix}
\; \theta = \begin{bmatrix}
0.0003 \\
0.0140 \\ 
0.0130 \\
\end{bmatrix}
$$

$$h(x^{(i)}, \theta) = \dfrac{1}{1 + e^{-\theta^T x^{(i)}}}$$

[[LR; Training]]

