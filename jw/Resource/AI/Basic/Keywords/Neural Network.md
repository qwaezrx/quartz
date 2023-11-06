#AI  

- Neural network is a particular kind of [[Machine learning]]
- Neural networks are special because they are highly flexible, which means they can solve an unusually wide range of problems just by finding the right weights

## Representation

![[NN_representation.jpeg]]

$$
a^{[l] \to \text{layer}}_{i \to \text{node in layer}}
$$

__Input layer__
$$
\begin{align}
& x_{1}, x_{2}, x_{3}, \dots, x_{n_{x}}
\end{align}
$$
__Hidden & Output layer__
$$
\begin{align}
& \mathbf{X} = \mathbb{R}^{n_{x} \times m} \\
& \mathbf{W}^{[1]} = \mathbb{R}^{n_{1}\times n_{x}} \\
& \mathbf{b}^{[1]} = \mathbb{R}^{n_{1} \times 1} \\
\\
& \mathbf{W}^{[2]} = \mathbb{R}^{1 \times n_{1}}  \\
& \mathbf{b}^{[2]} = \mathbb{R}^{1 \times 1}  \\
\\
& \mathbf{A}^{[1]} = \sigma(\mathbf{W}^{[1]} \cdot \mathbf{X} + \mathbf{b}^{[1]}) = \mathbb{R}^{n_{1} \times m} \\
& \mathbf{A}^{[2]} = \sigma(\mathbf{W}^{[2]} \cdot \mathbf{A}^{[1]} + \mathbf{b}^{[2]}) = \mathbb{R}^{1 \times m} = \hat{y}
\end{align}
$$

## Forward propagation
$$
\begin{align}

& \mathbf{Z}^{[l]} = \mathbf{W}^{[l]} \cdot \mathbf{A}^{[l-1]} + \mathbf{b}^{[l]} \\
& \mathbf{A}^{[l]} = g^{[l]}(\mathbf{Z}^{[l]}) \\
 \\ \hline
\\
& \mathbf{A}^{[l]} = \mathbb{R}^{n_{l} \times m} \\
& \mathbf{W}^{[l]} = \mathbb{R}^{n_{l} \times n_{l-1}} \\
& \mathbf{b}^{[l]} = \mathbb{R}^{n_{l} \times 1}  \\
\\
& n_{0} = n_{x}  \\
& \mathbf{A}^{[0]} = \mathbf{X} = \mathbb{R}^{n_{x} \times m}
\end{align}
$$

## Back propagation


## See more
- [Implementing a Neural Network from Scratch in Python – An Introduction](https://github.com/dennybritz/nn-from-scratch)
- [Why normalize images by subtracting dataset's image mean, instead of the current image mean in deep learning?](https://stats.stackexchange.com/questions/211436/why-normalize-images-by-subtracting-datasets-image-mean-instead-of-the-current) (Stack Exchange)
- [CS231n: Convolutional Neural Networks for Visual Recognition](https://cs231n.github.io/neural-networks-case-study/) (Stanford University)
- 