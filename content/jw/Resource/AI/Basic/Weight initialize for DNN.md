

[[DNN]]

### He initialization:

$$
W^{[l]} = \text{np.random.randn(shape)} * \text{np.sqrt}\left( \frac{2}{n^{[l-1]}} \right) 
$$


>[!note]
>Usually used with  [[ReLU]]

- Helps solve [[Vanishing, exploding gradients]] problem.

## Other variants: 
### Xavier initialization:
$$
\begin{align}
& \tanh \sqrt{ \frac{1}{n^{[l-1]}} } \\ \\
\end{align}
$$
### Others:

$$\sqrt{ \frac{2}{n^{[l-1]} + n^{[l]}} }$$

