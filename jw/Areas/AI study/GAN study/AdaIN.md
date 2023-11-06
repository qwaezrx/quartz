
## Adaptive Instance Normalization
$$
\begin{align}
& \text{AdaIN}(\mathbf{x}_{i}, \mathbf{y}) = \mathbf{y}_{s, i} \frac{{\mathbf{x}_{i} - \mu(\mathbf{x}_{i})}}{\sigma(\mathbf{x_{i}})} + \mathbf{y}_{b, i}
\end{align}
$$

where each feature map $\mathbf{x}_{i}$ is normalized separately, and then scaled and biased using the corresponding scalar components from style $\mathbf{y}$ The dimensionality of $\mathbf{y}$ is twice the number of feature maps on that layer.


## Usage
- [[StyleGAN]]