
[[Transformer#Transformer Issues]]


## Reversible Residual Layers


![[Pasted image 20230908204446.png]]


Dont have to cache activations for the backward pass


## Reversible layers equations

![[Pasted image 20230908210241.png]]

__Standard Transformer__:
$$
\begin{align}
& y_{a} = x + \text{Attention}(x) & y_{b} = y_{a} + \text{FeedFwd}(y_{a})
\end{align}
$$

__Reversible__:
$$
\begin{align}
& y_{1} = x_{1} + \text{Attention}(x_{2}) & y_{2} = x_{2} + \text{FeedFwd}(y_{1})
\end{align}
$$

__Recompute $x_{1}, x_{2}$ from $y_{1}, y_{2}$__:
$$
\begin{align}
& x_{1} = y_{1} - \text{Attention}(x_{2}) & x_{2} = y_{2} - \text{FeedFwd}(y_{1})
\end{align}
$$


![[Pasted image 20230908205108.png]]


