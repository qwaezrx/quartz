---
tags:
  - AI/Metric/NLP
---

- Pretty good single number evaluation metric
- Usually used on [[Machine translation]], [[Image captioning]] ...
- Not used to speech recognition


## Bilingual Evaluation Understudy

![[IMG_58E4C92CD5C4-1.jpeg]]

![[IMG_6217B704F475-1.jpeg]]

$$
\begin{align}
& P_{1} = \frac{{\sum_{\text{unigrams} \in \hat{y}}\text{Countclip}(\text{unigram})}}{\sum_{\text{unigrams} \in \hat{y}}\text{Count}(\text{unigram})} \\ \\

& P_{n} = \frac{{\sum_{\text{n-grams} \in  \hat{y}}\text{Countclip}(\text{n-gram})}}{\sum_{\text{n-grams} \in \hat{y}}\text{Count}(\text{n-gram})}
\end{align} 
$$

## Bleu details
$$
\begin{align}
& p_{n} = \text{Bleu score on n-grams only} \\
& \text{Combined Bleu score:} BP\exp\left( \frac{1}{4}\sum^{4}_{n=1}p_{n} \right) \\
& BP = \text{browny penalty} \\
& (\text{MT output length} > \text{reference output length}) \implies (BP = 1) \\
& \text{Otherwise} \implies \left( BP = \exp\left( 1-\frac{\text{reference output length}}{\text{MT output length}} \right) \right)
\end{align}
$$


