---
tags:
  - Paper_review
  - AI/GAI/LLM
---

(2307)

Paper: https://arxiv.org/pdf/2307.02486.pdf


![[Screenshot 2023-09-18 at 6.36.30 PM.png]]


# 1. Introduction
Recent years have witnessed a trend toward scaling NNs. The depth is primarily scaled up for exponential expressively, producing many powerful deep networks. The depth is primarily scaled up for exponential expressivity, producing many powerful deep networks.

Then, the sparse [[MoE]] models and model parallelism approaches efficiently enlarge the hidden dimension. Sequence length, as the last atomic dimension of the NN, is desirable to be unlimited. 

The major challenge of scaling up sequence length is striking the right balance between the computational complexity and the model expressivity. RNN-style models are primarily implemented to increase the length. However, its sequential nature limits the parallelization during training, which is essential in long-sequence modeling. It can operate as a CNN during training, and transform to an efficient RNN at test time. While they perform well at long-range benchmarks, their performance on regular lengths is not as good as Transformers, limited mainly by the model expressivity.

Another stand of scaling the sequence length is to decrease the complexity of Transformers, i.e. the quadratic complexity of self-attention. Implementing sliding windows or convolution modules over the attention is a straightforward way to make the complexity nearly linear. Nevertheless, this sacrifices the ability to recall the early tokens, forgetting the prompts at the very beginning of the sequence. 

Sparse attention reduces the computation by sparsifying the attention matrix, preserving the possibility of recalling long-distant information. For example, obtains $O(N\sqrt{ N }d)$ time complexity with a fixed sparse pattern. Besides the heuristic patterns, the learnable patterns prove to be useful for sparse attention.

![[Screenshot 2023-09-18 at 7.15.47 PM.png]]

Our solution is ___LongNet___, which replaces the attention of vanilla Transformers with a novel component named _dilated attention_. The general design principle is:
- _attention allocation decreases exponentially as the distance between tokens grows._
We prove that it obtains a linear computation complexity and a logarithm dependency between tokens. This deals with the contradiction between limited attention resources and accessibility to every token. In the implementation ___LongNet___ can be transformed into a dense Transformer, which seamlessly supports the off-the-shelf optimization for Transformers. Taking advantage of the linear complexity, ___LongNet___ can parallelize the training across nodes, breaking the constraint of both computation and memory with a distributed algorithm. This allows use to efficiently scale up the sequence length to 1B tokens with nearly constant runtime.

# 2. LongNet
## 2.1. Preliminary
Self-attention struggles with long sequences, due to its quadratic dependency on the sequence length. One query would attend to all keys and values, leading to computational inefficiencies.

[[Sparse attention]]  alleviates this issue by restricting the query's access to a subset of keys and values. The key of sparse attention is the sparse attention pattern $S \in \{ 0, 1 \}^{N \times N}$, which determines specific keys and values that the query $Q$ can attend to.
$$
O = \text{softmax}(QK^{T} \times \mathbb{1}_{S})V
$$

## 2.2 Dialated Attention
Dialated attention splits the input $(Q, K, V)$ into segments $\{ (\tilde{Q}_{i}, \tilde{K}_{i}, \tilde{V}_{i}) \}^{N/w}$ equally with a segment length $w$. Each segment is then sparsified along the sequence dimension by selecting the rows with an interval $r$. The computation can be written as:
$$
\begin{align}
& \tilde{Q}_{i} = [Q_{iw}, Q_{iw + r}, Q_{iw + 2r}, \dots, Q_{(i+1)w-1}] \\
& \tilde{K}_{i} = [K_{iw}, K_{iw + r}, K_{iw + 2r}, \dots, K_{(i+1)w-1}] \\
& \tilde{V}_{i} = [V_{iw}, V_{iw + r}, V_{iw + 2r}, \dots, V_{(i+1)w-1}] \\
 
\end{align}
$$

$$
\begin{align}
& \tilde{Q}_{i} = \text{softmax}(\tilde{Q}_{i}\tilde{K}^{T}_{i})\tilde{V}_{i}  \\
& \hat{O}_{i} = \{ \tilde{O}_{i, j} \mid j \text{ mod } r = 0;0\mid j \text{ mod } r \neq 0 \} \\
& O = \left[ \hat{O}_{0}, \hat{O}_{1}, \dots , \hat{O}_{\frac{N}{w}-1} \right]
\end{align}
$$

The dialated attention can be transformed into dense attention between a gathering operation over the input $(Q, K, V)$ and a scattering operation over the output $\tilde{O}_{i}$, so it can directly reuse any optimization for vanilla attention. Dilated attention can significantly reduce the computation cost by a factor of $\frac{N}{w}r^{2}$ over the vanilla attention.

![[Screenshot 2023-09-18 at 10.12.24 PM.png]]

In practice, the segment size $w$ trades the globality of attention for efficiency, while the dilation with a size r reduces the computation cost by approximating the attention matrix. To capture both long-range and short-range information efficiently, we implement a mixture of dilated attentions with different segment sizes and dilation rates $\{ r_{i}, w_{i} \}^{k}$
$$
\begin{align}
O = \sum^{k}_{i=1}\alpha_{i}O|_{r_{i}, w_{i}} \\
\alpha_{i} = \frac{s_{i}}{\sum_{j}s_{j}}
\end{align}
$$

![[Screenshot 2023-09-19 at 12.27.26 AM.png]]


![[Screenshot 2023-09-19 at 12.30.17 AM.png]]


![[Screenshot 2023-09-19 at 12.32.18 AM.png]]


![[Screenshot 2023-09-19 at 12.38.13 AM.png]]