#AI 

>[[NN]] with more than one hidden layers



![[IMG_D2AC1EC01B76-1.jpeg]]

DNNs are [[Neural Network]]s with multiple hidden layers.

DNNs can compute mathematical functions that are much easier to compute with deep networks than shallow networks.

Logistic regression: shallow

The main difference between the "classical" [[Machine learning]] and Deep learning is that Deep learning models "figure out" the best features using hidden layers.
# Deep L-layer Neural network
## Deep neural network notation

![[IMG_79D6F15F79B9-1.jpeg]]

- $L = 4$ (#layers)
- $n^{[l]}$ = number of units in layer $l$ 
	- $n^{[1]} = 5, n^{[2]} = 5, n^{[3]} = 3, n^{[4]} = 1$
	- $n^{[0]} = n_{x} = 3$
- $a^{[l]}$ = activations in layer $l$
	- $a^{[l]} = g^{[l]}(z^{[l]})$
- $W^{[l]}, b^{[l]}$ = weights and bias for $Z^{[l]}$

[[Neural Network#Forward propagation]]

## Getting your matrix dimensions right
- $W^{[l]}$.shape = $dW^{[l]}$.shape = $(n^{[l]}, n^{[l-1]})$
- $A^{[l]}$.shape = $Z^{[l]}$.shape = $dA^{[l]}$.shape = $dZ^{[l]}$.shape =$(n^{[l-1]}, m)$
- $b^{[l]}$.shape = $db^{[l]}$.shape = $(n^{[l]}, 1)$

## Forward and backward functions

![[Screenshot 2023-08-25 at 5.11.34 AM.png]]


![[Pasted image 20230826111342.png]]


## Forward propagation for layer $l$
- Input: $A^{[l-1]}$
- Output: $A^{[l]}$, cache($Z^{[l]}, W^{[l]}, b^{[l]}$)
$$
\begin{align}
& Z^{[l]} = W^{[l]}A^{[l-1]} + b^{[l]} \\
& A^{[l]} = g^{[l]}(Z^{[l]}) 
\end{align}
$$

## Back propagation for layer $l$
- Input: $dA^{[l]}$
- Output: $dA^{[l-1]}, dW^{[l]}, db^{[l]}$
$$
\begin{align}
& dZ^{[l]} = dA^{[l]} * g^{[l]}{'}(Z^{[l]}) \\
& dW^{[l]} = dZ^{[l]} A^{[l-1]T}  \\
& db^{[l]} = \frac{1}{m} \text{np.sum}(dZ^{[l]}, \text{axis=1, keepdims=True})  \\
& dA^{[l-1]} = W^{[l]T}dZ^{[l]}  \\
& \text{Note that * means element-wise multiplication} \\
& dZ^{[l]} = W^{[l+1]T}dZ^{[l+1]} * g^{[l]}{'}(Z^{[l]})
\end{align}
$$

