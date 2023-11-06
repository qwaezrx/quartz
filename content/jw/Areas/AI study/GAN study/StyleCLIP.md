---
tags:
  - AI/GAI/CV/GAN/StyleGAN
---

- Based on [[StyleGAN]]
- Follows Encoder-Decoder structure
	- text encoder to encode instructions
	- image decoder to synthesize new image
- used contrastive learning to align the text and image features.
	- maximize the similarity between text, image features
	- minimize the similarity between different different text and image pairs
- Able to learn more effective mapping between text and image features, resulting in higher-quality image synthesis.