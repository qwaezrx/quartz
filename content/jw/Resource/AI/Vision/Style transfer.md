---
tags:
  - AI/CV
---



![[Screenshot 2023-09-15 at 3.35.28 AM.png]]

## Loss in Style Transfer
$$
\begin{align}
& \mathcal{L}_{total}(\vec{p}, \vec{a}, \vec{x}) = \alpha \mathcal{L}_{content}(\vec{p}, \vec{x}) + \beta \mathcal{L}_{style}(\vec{p}, \vec{a}) \\ \\
& \vec{p}: \text{Content Image (Original photograph)} \\
& \vec{a}: \text{Style Image} \\
& \vec{x}: \text{Generated Image}
\end{align}
$$

#### __Content Loss__
![[Screenshot 2023-09-15 at 3.51.21 AM.png]]

$$
\mathcal{L}_{content}(\vec{p}, \vec{x}, l) = \frac{1}{2}\sum_{i, j}(F^{l}_{i, j} - P^{l}_{i, j})^{2}
$$

$$
\begin{align}
& J_{\text{content}}(C, G) = \frac{1}{4 \times n_{H}\times n_{W}\times n_{C}} \sum_{\text{all entires}} (a^{(C)} - a^{(G)})^{2}
\end{align}
$$


#### __Style Loss__
![[Screenshot 2023-09-15 at 3.54.58 AM.png]]

$$
G^{l}_{i, j} = \sum_{k}F^{l}_{ik}F^{l}_{jk}
$$

$$
\begin{align}
J^{[l]}_{\text{style}}(S, G) = \frac{1}{4 \times n_{C}^{2} \times (n_{H} \times n_{W})^{2}}\sum^{n_{C}}_{i=1}\sum^{n_{C}}_{j=1}(G^{(S)}_{\text{(gram)i,j}} - G^{(G)}_{\text{(gram)i,j}})^{2}
\end{align}
$$
- $G^{(S)}_{\text{gram}}$ : Gram matrix of the "style" image
- $G^{(G)}_{\text{gram}}$: Gram matrix of the "generated" image
- Make sure you remember that this cost is computed using the hidden layer activations for a particular hidden layer in the network $a^{[l]}$

__Gram matrix__
![[Pasted image 20230905023939.png]]

__Gram matrix - In Practice__
```python
def gram_matrix(input_tensor):
	input_tensorT = tf.transpose(input_tensor, perm[0, 2, 1, 3])
	result = tf.linalg.einsum('bijc,bijd->bcd', input_tensorT, input_tensor)
	input_shape = tf.shape(input_tensor)
	num_locations = tf.cast(input_shape[1] * input_shape[2], tf.float32)
	return result / num_locations
```


## See More

- [Perceptual Losses for Real-Time Style Transfer and Super-Resolution](https://cs.stanford.edu/people/jcjohns/eccv16/) (Johnson, Alahi & Li, 2016)

- [Visualizing and Understanding Convolutional Networks](https://arxiv.org/pdf/1311.2901.pdf) (Zeiler & Fergus, 2013)

- https://colab.research.google.com/github/https-deeplearning-ai/tensorflow-3-public/blob/main/Course%204%20-%20Generative%20Deep%20Learning/W1/ungraded_labs/C4_W1_Lab_1_Neural_Style_Transfer.ipynb#scrollTo=Jt3i3RRrJiOX

