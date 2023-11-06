---
tags:
  - "#Open_Source"
  - AI/GAI/CV/Diffusion
author: Stability.AI
date: 2022-08-22
GPU-hours: "150000"
cost: "600000"
parameters: 860000000
---

## Introduction

>[!Stable Diffusion]
>SD is a text-conditioned [[Diffusion Model#Improving Efficiency Latent Diffusion]] model

- Consists of 3 parts:
	- [[VAE]]
	- [[U-Net]]
	- Text Encoder(Optional)


![[Pasted image 20231017025610.png]]


![[Pasted image 20231017025635.png]]


## Text Encoder; SD

In [[U-Net]], given a noisy version of an image, the model is tasked with predicting the denoised version based on additional clues such as a class label. In the case of SD, the additional _clue_ is the text prompt.

At inference time, we can feed the description of an image we'd like to see and some pure noise as a starting point, and the model does its best to denote the random input into something that matches the caption.

![[Pasted image 20230910210453.png]]

SD leverages a pre-trained transformer model based on [[CLIP]].

The text encoder is a [[Transformer]] model that takes in a sequence of tokens and produces a 1024-dimensional vector for each token (0r 768-dimensional in the case of SD 1.0).

Instead of combining these vectors into a single representation, we keep them separate and use them as conditioning for the [[U-Net]]. -> allows the U-Net to make use of the information in each token separately, rather than just the overall meaning of the entire prompt.

often called as "encoder hidden states"

![[Pasted image 20230910225340.png]]


## VAE with SD

Like the text encoder, the [[VAE]] is usually trained separately and used as a frozen component during the diffusion model training and sampling process.

![[Pasted image 20230910233214.png]]

__Input__: (512, 512)
![[Pasted image 20230910233535.png]]

__Compressed__: (1, 4, 64, 64)
![[Screenshot 2023-09-10 at 11.35.23 PM.png]]

__Decompressed (Output)__: (512, 512)
![[Pasted image 20230910233610.png]]

## U-Net (Diffusion) with SD

[[Diffusion Model]]

The U-Net in SD takes in a 4-channel latent instead of 3-channel image as input.
The timestep embedding is fed in in the same way as the class conditioning. But this U-Net also needs to accept the text embeddings as additional conditioning.

Scattered throughout the U-Net are cross-attention layers. Each spatial location in the U-Net can _attend_ to different tokens in the text conditioning, bringing in relevant information from the prompt.


![[Pasted image 20230910234137.png]]

The U-Net for SD v1, v2 has around 860M parameters. The more recent SD XL has even more, at around, with most of the additional parameters being added at the lower-resolution stages via additional channels in the residual blocks (N vs 1280 in the original) and additional transformer blocks.


## Feeding Text Information into Generation Process

To make text a part of the image generation process, we have to adjust our noise predictor to use the text as input.

![[Pasted image 20230916014453.png]]


Our dataset now includes the encoded text. Since we're operating in the latent space, both the input images and predicted noise are in the latent space.

![[Pasted image 20230916014612.png]]

#### Layers of the U-Net Noise Predictor (without text)
![[Pasted image 20230916015318.png]]

Inside, we see that:
- The [[U-Net]] is a series of layers that work on transforming the latents array
- Each layer operates on the output of the previous layer
- Some of the outputs are fed (via [[Residual Connection]]s into the processing later in the network
- The timestep is transformed into a time step embedding vector, and that's what gets used in the layers
![[Pasted image 20230916015503.png]]

#### Layers of the U-Net Noise Predictor with Text
![[Pasted image 20230916015647.png]]

The main change to the system we need to add support for text inputs (technical term: text conditioning) is to add an attention layer between the [[ResNet]] blocks.

![[Pasted image 20230916015816.png]]

Note that the ResNet blocks doesn't directly look at the text. But the attention layers merge those text representations in the latents. And now the next ResNet can utilize that incorporated text information in its processing.

## Training Data for Text-To-Image Models (TBD)


## Illustrated SD


![[Pasted image 20230916010352.png]]


![[Pasted image 20230916010329.png]]


![[Pasted image 20230916010317.png]]


## Adding Context


![[Pasted image 20231010024227.png]]


## See more
- https://en.wikipedia.org/wiki/Stable_Diffusion

How to use:
- https://github.com/AUTOMATIC1111/stable-diffusion-webui
- https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Online-Services

How it works:
- https://jalammar.github.io/illustrated-stable-diffusion/
- https://huggingface.co/blog/stable_diffusion
- [High-Resolution Image Synthesis with Latent Diffusion Models](https://ommer-lab.com/research/latent-diffusion-models/) [The Stable Diffusion paper]
- For a more in-depth look at the algorithms and math, see Lilian Weng’s [What are Diffusion Models?](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/)

