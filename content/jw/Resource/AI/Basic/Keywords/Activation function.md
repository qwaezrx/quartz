When you build a [[Neural Network]], one of the choices you get to make is what activation function to use in the hidden layers.

Without non-linear activation function, all your neural network is doing is just computing a linear functions.

- Activation functions can be different in different layers.
# Different types of activation functions
## [[Sigmoid]] function
$$
a = \frac{1}{1 + e^{-z}}
$$
>[!warning]
>Don't use much in real world (use tanh instead).
>Only use in output layer


## [[Tanh]] function
$$
a = \tanh(z) = \frac{{e^{z} - e^{-z}}}{e^{z} + e^{-z}}
$$
>[!note]
>Almost always works better than the _Sigmoid function_.	

### Tanh derivative
$$
\begin{align}
g'(z) = 1 - (\tanh(z))^{2}
\end{align}
$$

## [[ReLU]]
Mostly the default of activation function
$$
a = max(0, z)
$$
### ReLU derivative
$$
\begin{align}
g'(z) = \left\{ \begin{array}{1}
0 \quad \text{if } z<0  \\
1 \quad \text{if } z\geq 0
\end{array}
\right.
\end{align}
$$


## Leaky ReLU
Usually works better than ReLU but not used much in real world.
$$
a = max(0.01z, z)
$$

### [[Leaky ReLU]] derivative
$$
\begin{align}
g'(z) = \left\{ \begin{array}{1}
0.01 \quad \text{if } z<0  \\
1 \quad \text{if } z\geq 0
\end{array}
\right.
\end{align}
$$