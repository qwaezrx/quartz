---
backbone: Transformer
tags:
  - AI/Transformer/Encoder
aliases:
  - Bidirectional Encoder Representations from Transformers
parameters: 340000000
author: Google
date: 2018-10-11
---

- Encoder only [[Transformer]]
- Open source ML framework for [[NLP]]


![[Screenshot 2023-09-08 at 2.48.39 AM.png]]


![[Screenshot 2023-09-08 at 2.48.02 AM.png]]


- [[Encoder Model|Masked Language Modeling]]
- Choose 15% of the tokens at random: mask them 80% of the time, replace them with a random token 10% of the time, or keep as 10% of the time.
- There could be multiple masked spans in a sentence
- Next sentence prediction is also used when pre-training



![[Screenshot 2023-09-08 at 3.06.20 AM.png]]

- [[<CLS>]]: a special classification symbol added in front of every input
- [[<SEP>]]: a special separator token

![[Pasted image 20230908030917.png]]

## BERT fine-tuning


![[Pasted image 20230908031505.png]]


