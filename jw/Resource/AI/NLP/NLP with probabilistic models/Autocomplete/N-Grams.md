---
tags:
  - AI/NLP
---


>A _N-gram_ is a sequence of _N_ words


N-grams are fundamental concepts in NLP. You can use them in [[Speech recognition]], [[spelling correction]], augmentative communication


Corpus: I am happy because I am learning
	Unigrams: { I, am, happy, because, learning }
	Bigrams: { I am, am happy, happy because, ... }
	Trigrams: { I am happy, am happy because, ... }


#### Bigram probability
Corpus: I am happy because I am learning
$$
\begin{align}
P(\text{am} \mid \text{I}) = \frac{C(\text{I am})}{C(\text{I})} = \frac{2}{2} = 1
\end{align}
$$

$$
\begin{align}
P(y\mid x) = \frac{C(x\;y)}{\sum_{w} C(x \; w)} = \frac{C(x\;y)}{C(x)}
\end{align}
$$

#### Trigram probability
Corpus: I am happy because I am learning
$$
\begin{align}
P(\text{happy} \mid \text{I am}) = \frac{C(\text{I am happy})}{C(\text{I am})} = \frac{1}{2}
\end{align}
$$
$$
\begin{align}
& 
P(w_{3}\mid w^{2}_{1}) = \frac{{C(w^{2}_{1} \; w_{3})}}{C(w^{2}_{1})}  \\
& C(w^{2}_{1} \; w_{3}) = C(w_{1} \;, w_{2} \;, w_{3}) = C(w^{3}_{1})
\end{align}
$$

#### N-gram probability
$$
\begin{align}
& P(w_{N}\mid w_{1}^{N-1}) = \frac{{C(w_{1}^{N-1} \; w_{N})}}{C(w_{1}^{N-1})}   \\
& C(w^{N-1}_{1} \; w_{N}) = C(w^{N}_{1})
\end{align}
$$


## Problems of N-grams
Problem: [[N-Grams]] made of known words still might be missing in the training corpus

![[Screenshot 2023-09-06 at 12.39.08 AM.png]]

Solutions:
- [[Smoothing]]
- Backoff
	- If N-gram missing => use (N-1)-gram, ...
		- Probability discounting e.g. Katz backoff
		- "Stupid" backoff
- Interpolation$P^(wn​∣wn−2​wn−1​)=λ1​×P(wn​∣wn−2​wn−1​)+λ2​×P(wn​∣wn−1​)+λ3​×P(wn​)​$Where $∑_i​λ_i​=1$

