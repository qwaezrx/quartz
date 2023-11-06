---
tags:
  - AI/GRU
---

## Gated Recurrent Unit

![[Pasted image 20230906155047.png]]

- GRUs "decide" how to update the hidden state
- GRUs help preserve important information
- Slower than [[RNN]]


## GRU (simplified)
$$
\begin{align}
& c : \text{memory cell} \\
& \Gamma : \text{gate}  & \Gamma_{u}: \text{update gate} \\
& c^{<t>} = a^{<t>}  \\ \\

& \tilde{c}^{<t>} = \tanh(W_{c}[c^{<t-1>}, x^{<t>}] + b_{c}) \\
 & \Gamma_{u} = \sigma(W_{u}[c^{<t-1>}, x^{<t>}] + b_{u})\\
& c^{<t>} =  \Gamma_{u} * \tilde{c}^{<t>} + (1-\Gamma_{u}) *c^{<t-1>}

\end{align}
$$

## GRU (full)
[[GRU unit (full).canvas|GRU unit(full)]]

$$
\begin{align}
& c : \text{memory cell} \\
& \Gamma_{r} : \text{relevance gate}  & \Gamma_{u}: \text{update gate} \\
& c^{<t>} = a^{<t>}  \\ \\

 & \Gamma_{r} = \sigma(W_{r}[c^{<t-1>}, x^{<t>}] + b_{r})\\
 & \Gamma_{u} = \sigma(W_{u}[c^{<t-1>}, x^{<t>}] + b_{u})\\ \\

& \tilde{c}^{<t>} = \tanh(W_{c}[\Gamma_{r} * c^{<t-1>}, x^{<t>}] + b_{c}) \\
 \\
& c^{<t>} =  \Gamma_{u} * \tilde{c}^{<t>} + (1-\Gamma_{u}) *c^{<t-1>}

\end{align}
$$




## GRU; Forward propagation

[[def forward_V_GRU()]]


