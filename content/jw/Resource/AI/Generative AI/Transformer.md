---
author: Google
tags:
  - AI/Transformer
  - Paper_review
date: 2017-12-06
---

Paper: [Attention Is All You Need](https://arxiv.org/abs/1706.03762) 

## Advantages of Transformer architecture
- Scale efficiency
	- Can be scaled efficiently to use multi core [[GPU]]s
- [[Parallel process]]
	- Can parallel process input data, making use of much large training dataset.
- Attention to input meaning
	- Able to learn to pay attention to the meanings of words it's processing
- Can ingest the full sequence

## Intuition
- [[Attention model]] + [[CNN]] style
	- [[Self-attention]]
	- [[Multi-head attention]]
		- For loop of self-attention


## Transformer model

[[Positional encoding]]

[[Multi-head attention]]


![[Screenshot 2023-09-04 at 6.41.17 PM.png]]

![[Pasted image 20230908020238.png]]


#### Transformer; Encoder block

![[Pasted image 20230908035337.png]]


#### Transformer; Decoder block

![[Pasted image 20230908020212.png]]


## Transformer Issues

- Attention on sequence of length $L$ takes $L^2$ time and memory![[Screenshot 2023-09-08 at 4.08.43 AM.png]]
- $N$ layers take $N$ times as much memory
	- [[GPT-3]] has 96 layers

#### Attention complexity
- Q, K, V are all (L, d_model)
- $QK^{T}$ is (L, L)
- Save compute by using area of interest for large $L$


#### Memory with N layers
- Activations need to be stored for bachprop

![[Pasted image 20230908204323.png]]


## Transformer based Models

![[Pasted image 20231016033928.png]]

```dataview
TABLE date, parameters, author
FROM #AI/Model AND #Transformer OR #AI/Transformer  
SORT date DESC
```


## See More
- [History of Generative AI(Arxiv)](https://arxiv.org/pdf/2303.04226.pdf)
- [Attention Is All You Need](https://arxiv.org/abs/1706.03762) (Vaswani, Shazeer, Parmar, Uszkoreit, Jones, Gomez, Kaiser & Polosukhin, 2017)