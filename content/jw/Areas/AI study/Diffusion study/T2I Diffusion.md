---
tags:
  - AI/CV
---


[[Diffusion Model]](DM) is the _de facto_ workhorse for T2I generation. Diffusion-based T2I models generate photorealistic images via iterative refinements. [[GLIDE]] introduced a cascade diffusion structure and utilized classifier-free guidance for image generation and editing. DALL-E2 proposed a model with several stages, encoding text with [[CLIP]], decoding images from text encoding, and upsampling them from $64^{2}$ to $1024^{2}$. [[Imagen]] discovered that scaling up the size of the text encoder improves both sample fidelity and text-image alignment.
[[VQ-Diffusion]] learned T2I diffusion models on the discrete latent space of VQ-VAE. The popular latent diffusion model ([[LDM]], _i.e._ [[Stable diffusion]]) investigated the diffusion process over the latent space of pre-trained encoders, improving both training and sampling efficiency without quality degradation.

Although [[GAN]]s and [[Autoregressive model]](AR) models show T2I capability to some extent, most of them generate images on specific domains instead of open world text sets.

With the advances of large-scale language encoder, GANs and AR models recently start to handle generation with arbitrary texts with promising qualities too.