---
tags:
  - AI/MoE
  - AI/Transformer/Decoder
author: Google
parameters: 1200000000000
date: 2021-12-13
---

- 7x larger than [[GPT-3]], 1/3 energy used
- 64 experts per layer
- activates only 95B parameters (8%)

## Difference between Transformer
- Positional encoding -> [[Per-layer relative bias]]
- linear projection & Activation function -> [[Gated Linear Unit]]
- LayerNorm -> [[RMSNorm]]

## Hyperparameters
- E: Number of experts in the MoE layer
- B: Mini-batch size
- S: Input sequence length. Input batch has B * S tokens
- M: Model or embedding dimension
- H: Hidden dimension of the feed-forward network
- L: Number of layers in the [[Transformer]] model
- N: The number of total devices


## See More
- [GLaM: Efficient Scaling of Language Models with Mixture-of-Experts(arXiv)](https://arxiv.org/abs/2112.06905)