---
tags:
  - AI/GAI
aliases:
  - Variational AutoEncoder
  - Variational Autoencoder
---

The latent representation of the data is more probabilistic in VAE so that the later output is partially determined by chance.

![[Pasted image 20231017004536.png]]

Instead of just the output from the encoder being in the latent space, will take two outputs from the encoder:
- Mean encoding
- Standard deviation of the encoding
We'll also generate noise using a Gaussian distribution so that our actual encoding will be sampled from the Gaussian distribution using our standard deviation, mean by multiplying out the noise by the standard deviation and then adding the result to the mean.

![[Pasted image 20230914083428.png]]

- VAE is able to generate new samples because of the variational latent space

VAE is less capable of making precise predictions at the pixel level (compared to [[U-Net]]), since the output must be entirely re-constructed from the low-dimensional latent space.
- Doesn't have 'skip-connections'


![[Pasted image 20230913040135.png]]


## Variational Auto-Encoder
- + VAEs can compress images to a smaller spatial dimension

[[AutoEncoder]]

_VAE architectural diagram_:
![[Pasted image 20230914042516.png]]



## Sampling Layer and Encoder

$$z = \mu + e^{0.5\sigma} * \epsilon $$


```python
class Sampling(tf.keras.layers.Layer):
	def call(self, inputs):
		mu, sigma = inputs
		batch = tf.shape(mu)[0]
		dim = tf.shape(mu)[1]
		epsilon = tf.keras.backend.random_normal(shape=(batch, dim))
		return mu + tf.exp(0.5 * sigma) * epsilon
```


```python
def encoder_model(LATENT_DIM, input_shape):
	inputs = tf.keras.layers.Input(input_shape)
	mu, sigma, conv_shape = encoder_layers(inputs, latent_dim=LATENT_DIM)
	z = Sampling()((mu, sigma))
	model = tf.keras.models.Model(inputs, outputs=[mu, sigma, z])
	return model, conv_shape
```


## Loss Function and Model Definition
#### KL Reconstruction Loss
[[KL-Divergence]]
```python
def kl_reconstruction_loss(mu, sigma):
	kl_loss = 1 + sigma - tf.square(mu) - tf.math.exp(sigma)
	return tf.reduce_sum(kl_loss) * -0.5
```



## Reparameterize in VAE
It allows for use to have a differentiable function that represents our sampling technique, which means we can backpropagate through this network


## See More

[1](https://learning.oreilly.com/library/view/generative-deep-learning/9781098134174/ch03.html#idm45387024580992-marker) Diederik P. Kingma and Max Welling, “Auto-Encoding Variational Bayes,” December 20, 2013, [_https://arxiv.org/abs/1312.6114_](https://arxiv.org/abs/1312.6114).

[2](https://learning.oreilly.com/library/view/generative-deep-learning/9781098134174/ch03.html#idm45387024036912-marker) Vincent Dumoulin and Francesco Visin, “A Guide to Convolution Arithmetic for Deep Learning,” January 12, 2018, [_https://arxiv.org/abs/1603.07285_](https://arxiv.org/abs/1603.07285).

Ziwei Liu et al., “Large-Scale CelebFaces Attributes (CelebA) Dataset,” 2015, [_http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html_](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html).

- [VAE MNIST - TF (Colab)](https://colab.research.google.com/github/https-deeplearning-ai/tensorflow-3-public/blob/main/Course%204%20-%20Generative%20Deep%20Learning/W3/ungraded_labs/C4_W3_Lab_1_VAE_MNIST.ipynb)

- [Convolutional VAE - TF (Official Colab Tutorial)](https://colab.research.google.com/github/tensorflow/docs/blob/master/site/en/tutorials/generative/cvae.ipynb)

- https://github.com/AntixK/PyTorch-VAE

- [Learning Latent Subspaces in Variational Autoencoders](https://proceedings.neurips.cc/paper_files/paper/2018/file/73e5080f0f3804cb9cf470a8ce895dac-Paper.pdf)