---
tags:
  - AI/NLP
---


Given a text, you can represent it as a vector of dimension $V$
$V$ = vocabulary size.
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/vpVZPKHCS6uVWTyhwmurrQ_d2e2fd874a354ab38047ef531021b681_Screen-Shot-2020-09-01-at-7.48.25-AM.png?expiry=1692748800000&hmac=_gcCeJ3yjR8aj1PBzyK1XT7FwiH8yJrVOn-RZ_FfeQ4)

As you can see, as $V$ gets larger, the vectors becomes more sparse.
-> more features
-> training more parameters ($\theta V$)
-> larger training time, prediction time

## Feature extraction
$freq$: dictionary mapping from (word, class) to frequency
$$X_m = [1, \sum_w freqs(w, 1), \sum_w freqs(w, 0)]$$
- $X_m$: Features of text m
- 1: bias
- $\sum_w freqs(w, 1)$: Sum Pos. Frequencies
- $\sum_w freqs(w, 0)$: Sum Neg. Frequencies

### Example: 
Positive texts:
- "I am happy because I am learning NLP",
- "I am happy"
Negative texts:
- "I am sad, I am not learning NLP"
- "I am sad"

$m$: "I am sad, I am not learning NLP" -> $X_m$: $[1, 8, 11]$




