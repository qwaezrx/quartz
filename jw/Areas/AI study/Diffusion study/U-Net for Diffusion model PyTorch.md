---
tags:
  - CS/Programming/Python/PyTorch
---

## U-Net for [[Diffusion Model]]
- More advanced than the original U-Net proposed in 2015 which additions like attention and residual blocks.

![[Screenshot 2023-09-09 at 9.22.54 PM.png]]

[[ContextUnet PyTorch]]

Here's how we might create a U-Net and feed our batch of noisy images through it:
```python
model = UNet2DModel(
	in_channels=3, # 3 channels for RGB images
	sample_size=64, # Specify our input size
	block_out_channels=(64, 128, 256, 512), # N channels per layer
	down_block_types=("DownBlock2D", "DownBlock2D",
					  "AttnDownBlock2D", "AttnDownBlock2D"),
	up_block_types=("AttnUpBLock2D", "AttnUpBlock2D",
					"UpBlock2D", "UpBlock2D"),
)

# Pass a batch of data through
with torch.no_grad():
	out = model(noised_x, timestep=timesteps).sample

out.shape # torch.Size([8, 3, 64, 64])
```


#### Training

For each training step, we:
- Load a batch of images
- Add noise to the images, choosing random timesteps to determine how much noise is added
- Feed the noisy images into the model
- Calculate the loss, which is the [[MSE]] between the model's predictions and the target - which in this case is the noise and that we added to the images. This is called the noise or 'epsilon' objective.
- Backpropagate the loss and update model parameters with optimizer

Here's how it looks like in code:
```python
num_epochs = 50
lr = 1e-4
model = model.to(device)
optimzier = torch.optim.AdamW(model.parameters(), lr=lr)
losses = []

for epoch in range(num_epochs):
	for step, batch in enumerate(train_dataloader):
		# Load the input images
		clean_images = batch["images"].to(device)
		
		# Sample noise to add to the images
		noise = torch.randn(clean_images.shape).to(clean_images.device)
		
		# Sample a random timestep for each image
		timesteps = torch.randint(
			0,
			scheduler.num_train_timesteps,
			(clean_images.shape[0]),
			device=clean_images.device,
		).long()
		
		# Add noise to clean images according timestep
		noisy_images = schedular.add_noise(clean_images, noise, timesteps)
		
		# Get the model prediction for the noise
		noise_pred = model(noisy_images, timesteps, return_dict=False)[0]
		
		# Compare the prediction with the actual noise:
		loss = F.mse_loss(noise_pred, noise)
		
		# Store the loss for later plotting
		losses.append(loss.item())
		
		# Update the model parameters with optimizer based on this loss
		loss.backward()
		optimizer.step()
		optimizer.zero_grad()


```


#### Sampling
```python
pipeline = DDPMPipeline(unet=model, scheduler=scheduler)
ims = pipeline(batch_size=4).images

show_images(ims, nrows=1)
```

Simple sampling loop:
```python
sample = torch.randn(4, 3, 64, 64).to(device)

for i, t in enumerate(scheduler.timesteps):
	# Get model pred
	with torch.no_grad():
		noise_pred = model(sample, t).sample
	
	# Update sample with step
	sample = scheduler.step(noise_pred, t, sample).pred_sample


show_images(sample.clip(-1, 1) * 0.5 + 0.5, nrows=1)
```

Which is same as:
```python
pipeline.scheduler.step()
```

#### Evaluation
Generative model performance can be evaluated using [[FID]] scores. FID score measures how closely generated samples match real-world samples by comparing statistics between feature maps extracted from both sets of data using a pre-trained neural network.
The lower the score -> the better the quality.


