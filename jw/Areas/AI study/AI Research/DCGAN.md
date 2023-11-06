---
tags:
  - AI/GAI/CV/GAN
---


## Deep Convolutional GAN

_Training the DCGAN:_
![[Pasted image 20230914192318.png]]


## MNIST Generation
![[Screenshot 2023-09-15 at 9.36.45 PM.png]]

Compared to [[GAN#MNIST Generation]]


## DCGAN in PyTorch
```python

class Hyperparameters:
	def __init__(self, **kwargs):
		self.__dict__.update(kwargs)


hp = Hyperparameters(
	n_epochs=200,
	batch_size=64,
	lr=0.0002,
	b1=0.5,
	b2=0.999,
	n_cpu=8,
	latent_dim=100,
	img_size=32,
	channels=1,
	sample_interval=400,
)


```

```python
class Generator(nn.Module):
	def __init__(self):
		super(Generator, self).__init__()
		self.init_size = hp.img_size // 4
		self.l1 = nn.Sequential(
			nn.Linear(hp.latent_dim, 128 * self.init_size ** 2)
		)
		self.conv_blocks = nn.Sequential(
			nn.BatchNorm2d(128),
			nn.Upsample(scale_factor=2),
			nn.Conv2d(128, 128, 3, stride=1, padding=1),
			nn.BatchNorm2d(128, 0.8),
			nn.LeakyReLU(0.2, inplace=True),
			nn.Upsample(scale_factor=2),
			nn.Conv2d(128, 64, 3, stride=1, padding=1),
			nn.BatchNorm2d(64, 0.8),
			nn.LeakyReLU(0.2, inplace=True),
			nn.Conv2d(64, hp.channels, 3, stride=1, padding=1),
			nn.Tanh(),
		)

	def forward(self, z):
		out = self.l1(z)
		out = out.view(out.shape[0], 128, self.init_size, self.init_size)
		img = self.conv_blocks(out)
		return img
```


```python
class Discriminator(nn.Module):
	def __init__(self):
		super(Discriminator, self).__init__()
		def discriminator_block(in_features, out_filters, bn=True):
			block = [
				nn.Conv2d(in_filters, out_filters, 3, 2, 1),
				nn.LeakyReLU(0.2, inplace=True),
				nn.Dropout2d(0.25),
			]
			if bn:
				block.append(nn.BatchNorm2d(out_filters, 0.8))
			return block
		self.model = nn.Sequential(
			*discriminator_block(hp.channels, 16, bn=False),
			*discriminator_block(16, 32),
			*discriminator_block(32, 64),
			*discriminator_block(64, 128),
		)
		# The height and width of downsampled image
		ds_size = hp.img_size // 2 ** 4
		self.adv_layer = nn.Sequential(
			nn.Linear(128 * ds_size ** 2, 1),
			nn.Sigmoid()
		)
	
	def forward(self, img):
		out = self.model(img)
		out = out.view(out.shape[0], -1)
		validity = self.adv_layer(out)
		return validity

```


#### Training
```python
loss_fn = torch.nn.BCELoss()

generator = Generator()

discriminator = Discriminator()

if cuda:

  generator.cuda()

  discriminator.cuda()

  loss_fn.cuda()

# Initialize weights

generator.apply(weights_init_normal)

discriminator.apply(weights_init_normal)
```

```python
for epoch in range(hp.n_epochs):

  for i, (imgs, _) in enumerate(dataloader):

      valid = Variable(Tensor(imgs.shape[0], 1).fill_(1.0), requires_grad=False)

      fake = Variable(Tensor(imgs.shape[0], 1).fill_(0.0), requires_grad=False)

      real_imgs = Variable(imgs.type(Tensor))

      optimizer_G.zero_grad()

      z = Variable(Tensor(np.random.normal(0, 1, (imgs.shape[0], hp.latent_dim))))

      gen_imgs = generator(z)

      g_loss = loss_fn(discriminator(gen_imgs), valid)

      g_loss.backward()

      optimizer_G.step()

      optimizer_D.zero_grad()

      real_loss = loss_fn(discriminator(real_imgs), valid)

      fake_loss = loss_fn(discriminator(gen_imgs.detach()), fake)

      d_loss = (real_loss + fake_loss) / 2

      d_loss.backward()

      optimizer_D.step()

      batches_done = epoch * len(dataloader) + i

      if batches_done % hp.sample_interval == 0:

        clear_output()

        print(f"Epoch:{epoch}:It{i}:DLoss{d_loss.item()}:GLoss{g_loss.item()}")

        visualize_output(gen_imgs.data[:50],10, 10)
```



## Generator Discriminator Expectation

![[Pasted image 20230916001454.png]]


## See More
- [First DCGAN - TF (Colab)](https://colab.research.google.com/github/https-deeplearning-ai/tensorflow-3-public/blob/main/Course%204%20-%20Generative%20Deep%20Learning/W4/ungraded_labs/C4_W4_Lab_2_First_DCGAN.ipynb)
- [DCGAN CelebA - TF (Colab)](https://colab.research.google.com/github/https-deeplearning-ai/tensorflow-3-public/blob/main/Course%204%20-%20Generative%20Deep%20Learning/W4/ungraded_labs/C4_W4_Lab_3_CelebA_GAN_Experiments.ipynb)