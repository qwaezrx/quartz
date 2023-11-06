---
tags:
  - CS/Programming/Python/PyTorch
---


![[Screenshot 2023-09-09 at 9.22.54 PM.png]]



## Diffusion model

```python
class ContextUnet(nn.Module):
	def __init__(self, in_channels, n_feat=256, n_cfeat=10, height=28):
		super(ContextUnet, self).__init__()
		self.in_channels = in_channels
		self.n_feat = n_feat
		self.n_cfeat = n_cfeat
		self.h = height
		
		# Initialize the intial convolutional layer
		self.init_conv = ResidualConvBlock(in_channels, 
										   n_feat, 
										   is_res=True)
		
		# Initialize the down-sampling path of the U-Net with two levels
		self.down1 = UnetDown(n_feat, n_feat)
		self.down2 = UnetDown(n_feat, 2 * n_feat)
		
		# original: self.to_vec = nn.Sequential(nn.AvgPool2d(7))
		self.to_vec = nn.Sequential(nn.AvgPool2D((4)), nn.GELU())
		
		# Embed the timestep and context labels with a one-layer fully connected network
		self.timeembed1 = EmbedFC(1, 2 * n_feat)
		self.timeembed2 = EmbedFC(1, 1 * n_feat)
		self.contextembed1 = EmbedFC(n_cfeat, 2 * n_feat)
		self.contextembed2 = EmbedFC(n_cfeat, 1 * n_feat)
		
		# Initialize the upscaling path of the U-Net with three levels
		self.up0 = nn.Sequential(
			nn.ConvTranspose2d(in_channels=2 * n_feat, 
							   out_channels=2 * n_feat, 
							   kernel_size=self.h // 4, 
							   stride=self.h // 4), # up-sample
			nn.GroupNorm(num_groups=8, 
						 num_channels=2 * n_feat),
			nn.ReLU(),
		)
		self.up1 = UnetUp(4 * n_feat, n_feat)
		self.up2 = UnetUp(2 * n_feat, n_feat)
		
		# Initialize the final convolutional layers to map to the same number of channels as the input image
		self.out = nn.Sequential(
			nn.Conv2d(in_channels=2 * n_feat, 
					  out_channels=n_feat, 
					  kernel_size=3, 
					  stride=1, 
					  padding=1),
			nn.GroupNorm(num_groups=8, 
						 num_channels=2 * n_feat),
			nn.ReLU(),
			nn.Conv2d(in_channels=n_feat,
					  out_channels=self.in_channels,
					  kernel_size=3,
					  stride=1,
					  padding=1),
		)
		
	def forward(self, x, t, c=None):
		"""
		x : (batch, n_feat, h, w) : input image
		t : (batch, n_cfeat)      : time step
		c : (batch, n_classes)    : context label
		"""
		# Context mask says which samples to block the context on
		
		
		# Pass the input image through the initial conv layer
		x = self.init_conv(x)
		# Pass the result through the down-sampling path
		down1 = self.down1(x)
		down2 = self.down2(x)
		
		# Convert the feature maps to a vector and apply an activation
		hiddenvec = self.to_vec(down2)
		
		# Mask out context if context_mask == 1
		if c is None:
			c = torch.zeros(x.shape[0], self.n_cfeat).to(x)
			
		# Embed context and timestep
		cemb1 = self.contextembed1(c).view(-1, self.n_feat * 2, 1, 1) # (batch, 2 * n_feat, 1, 1)
		temb1 = self.timeembed1(t).view(-1, self.n_feat * 2, 1, 1)
		cemb2 = self.contextembed2(c).view(-1, self.n_feat, 1, 1)
		temb2 = self.timeembed2(t).view(-1, self.n_feat, 1, 1)
		
		up1 = self.up0(hiddenvec)
		up2 = self.up1(cemb1 * up1 + temb1, down2)
		up3 = self.up2(cemb2 * up2 + temb2, down1)
		out = self.out(torch.cat(up3, x), 1)
		return out
		






```

## Diffusion hyperparameters

```python
# Diffusion hyperparameters
timesteps = 500
beta1 = 1e-4
beta2 = 0.02

# Network hyperparameters
device = torch.device("cuda:0") if torch.cuda.is_available() else torch.device("cpu")
n_feat = 64 # 64 hidden dimension features
n_cfeat = 5 # Context vector is of size 5
height = 16 # 16x16 image
save_dir = "./weights/"

```

## Construct [[DDPM]] noise schedule

```python
# construct DDPM noise schedule
b_t = (beta2 - beta1) * torch.linspace(0, 1, timesteps + 1, device=device) + beta1
a_t = 1 - b_t
ab_t = torch.cumsum(a_t.log(), dim=0).exp()    
ab_t[0] = 1
```

## Construct model

```python
nn_model = ContextUnet(
	in_channels=3,
	n_feat=n_feat,
	n_cfeat=n_cfeat,
	height=height,
)
```