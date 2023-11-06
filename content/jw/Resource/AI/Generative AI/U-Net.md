---
tags:
  - AI/CV
---


(2015)

> Used as _Noise predictor_ in [[Stable diffusion]]


Model for [[Semantic segmentation]] using [[Transpose convolutions]], where the desired output has the same spatial extent as the input. It consists of a series of 'downsampling' layers that reduce the spatial size of the input, followed by a series of 'upsampling' layers that increase the spatial extent of the input again.
The downsampling layers are also typically followed by a 'skip-connection' that connects the downsampling layer's output to the upsampling layer's input. This allows the upsampling layers to 'see' the higher-resolution representations from earlier in the network.

![[Screenshot 2023-09-03 at 9.45.38 PM.png]]


![[Pasted image 20230910200510.png]]

Basic U-Net in code:
```python
import torch.nn as nn

class BasicUNet(nn.Module):
	def __init__(self, in_channels, out_channels):
		super(BasicUNet, self).__init__()
		self.down_layers = torch.nn.ModuleList([
			nn.Conv2d(in_channels, 32, kernel_size=5, padding=2),
			nn.Conv2d(32, 64, kernel_size=5, padding=2),
			nn.Conv2d(64, 64, kernel_size=5, padding=2),
		])
		self.up_layers = torch.nn.ModuleList([
			nn.Conv2d(64, 64, kernel_size=5, padding=2),
			nn.Conv2d(64, 32, kernel_size=5, padding=2),
			nn.Conv2d(32, out_channels, kernel_size=5, padding=2),
		])
		
		self.activation = nn.SiLU()
		self.downscale = nn.MaxPool2d(2)
		self.upscale = nn.Upsample(scale_factor=2)
	
	def forward(self, x):
		h = []
		for i, l in enumerate(self.down_layers):
			x = self.activation(l(x))
			if i < 2:
				h.append(x)
				x = self.downscale(x)
		
		for i, l in enumerate(self.up_layers):
			if i > 0:
				x = self.upscale(x)
				x += h.pop()
			x = self.activation(l(x))
			
		return x


```


## Training U-Net


![[Pasted image 20230916010850.png]]



## Improving U-Net

- __Add more parameters__:
	- Using multiple conv layers in each block
	- Using larger number of filters in each conv layers
	- Make network deeper

- __Add residual connections__:
	- ResBlocks (instead of regular conv layers)
		- + can help the model learn more complex functions while keeping training stable

- __Add normalization__:
	- Batch normalization
		- + Can help the model learn more quickly and reliably

- __Add regularization__:
	- Dropout
		- + Prevent the model from overfitting

- __Add attention__:
	- Self-attention layers
		- + allow the model to focus on different parts of the image at different times
		- + transformer-like attention layers also lets us increase the number of learnable parameters.
		- - much more expensive to compute in higher resolutions
			- typically only use them at lower resolutions

- __Add additional input for timestep ([[Timestep conditioning]])__:
	- + model can tailor its predictions according to the noise level.
	- Used almost all recent diffusion models.


## See more
- [[Diffusion Model]]
- [[U-Net for Diffusion model PyTorch]]
- 
