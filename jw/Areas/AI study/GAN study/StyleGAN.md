---
tags:
  - AI/GAI/CV/GAN/StyleGAN
  - Paper_review
author: NVIDIA
date: 2019-05-29
---

Paper: [A Style-Based Generator Architecture for Generative Adversarial Networks](https://arxiv.org/pdf/1812.04948.pdf?ref=blog.promedius.ai)

- StyleGAN = [[PGGAN]] + Style transfer

StyleGAN improves [[GAN]]s by separating high-level attributes and variations, allowing for intuitive control and better performance in terms of quality metrics, interpolation, and disentanglement, focus on inverse mapping - projecting data back into the latent space, resulting in a useful feature representation for auxiliary discrimination tasks.

## Abstract
We propose an alternative generator architecture for [[GAN]]s, borrowing from style transfer literature. The new architecture leads to an automatically learned, unsupervised separation of high-level attributes (e.g. pose and identity when trained on human faces) and stochastic variation in the generated images (e.g. freckles, hair), and it enables intuitive, scale-specific control of the synthesis.


## Style-based generator
Traditionally the latent code is provided to the generator through an input layer, i.e.

![[Screenshot 2023-10-11 at 3.11.33 PM.png]]
_Figure 1. While the traditional generator feeds the latent code through the input layer only, we first map the input to an intermediate latent space $\mathcal{W}$ , which then controls the generator through adaptive instance normalization (AdaIN) at each convolution layer. Gaussian noise is added after each convolution, before evaluating the nonlinearity.
Here "A" stands for a learned affine transform, and "B" applies learned per-channel scaling factors to the noise input.
The mapping network $f$ consists of 8 layers and the synthesis network $g$ consists of 18 layers - two for each resolution ($4^{2} - 1024^{2}$). The output of the last layer is converted to RGB using a separate 1 x 1 convolution.
Generator has 26.2M trainable parameters compared to 23.1M in the traditional generator._

- $f: \mathcal{Z} \to \mathcal{W}$  first produces $\mathbf{w} \in \mathcal{W}$
	- $f$ is implemented using an 8-layer [[MLP]]
- Learned affine transformations then specialize $\mathbf{w}$ to _styles_ $\mathbf{y} = (\mathbf{y}_{s}, \mathbf{y}_{b})$
	- controls adaptive instance normalization ([[AdaIN]])
		- is particularly well suited for our purposes due to its efficiency and compact representation.
	- where each feature map $\mathbf{x}_{i}$ is normalized separately, and then scaled and biased using the corresponding scalar components from style $\mathbf{y}$
	- The dimensionality of $\mathbf{y}$ is twice the number of feature maps on that layer.
- Comparing our approach to style transfer, we compute the spatially invariant style $\mathbf{y}$ from vector $\mathbf{w}$ instead of an example image. 


![[Screenshot 2023-10-11 at 3.43.06 PM.png]]


### Quality of generated images

![[Screenshot 2023-10-11 at 3.46.26 PM.png]]


## Properties of the style-based generator
Our generator architecture makes it possible to control the image synthesis via scale-specific modifications to the styles. We can view the mapping network and affine transformations as a way to draw samples for each style from a learned distribution, and the synthesis network as a way to generate a novel image based on a collection of styles. The effects of each style are localized in the network, i.e., modifying a specific subset of the styles can be expected to affect only certain aspects of the image.

### Style mixing
To further encourage the styles to localize, we employ _mixing regularization_, where a given percentage of images are generated using two random latent codes instead of one during training. When generating such an image, we simply switch from one latent code to another - an operation we refer to as _style mixing_ - at a randomly selected point in the synthesis network. 
- we run two latent codes $\mathbf{z}_{1}, \mathbf{z}_{2}$ through the mapping network
- and have the corresponding $\mathbf{w}_{1}, \mathbf{w}_{2}$ control the styles
- $\mathbf{w}_{1}$ applies before the crossover point and $\mathbf{w}_{2}$ after it
This regularization technique prevents the network from assuming that adjacent styles are correlated.


![[Screenshot 2023-10-11 at 6.19.48 PM.png]]


![[Screenshot 2023-10-11 at 6.23.06 PM.png]]


### Stochastic variation


![[Screenshot 2023-10-11 at 6.23.30 PM.png]]


## Limitations
- [[Texture sticking]]
	- StyleGAN generators don't learn features "hierarchical" but in fixed pixel 
	- -> [[StyleGAN3]]
- 