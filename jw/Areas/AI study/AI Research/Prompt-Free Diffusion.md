---
tags:
  - Paper_review
  - AI/GAI/CV
---

[Paper](https://arxiv.org/abs/2305.16223)
[Github](https://github.com/SHI-Labs/Prompt-Free-Diffusion)


![[Screenshot 2023-10-10 at 7.35.05 PM.png]]
Figure 1: Given a pre-trained T2I diffusion model, __Prompt-Free Diffusion__ modifies it to intake a reference image as "context", an optional image structural conditioning, and an initial noise. No prompt needed: instead, the reference image governs the semantics and appearance, and the optional conditioning provides additional control over the structure.

## Abstract
__One pain point: the text prompt engineering__
Our proposed framework, __Prompt-Free Diffusion__, relies on __only visual inputs to generate new images__: it takes a reference image as "context", an optional image structure conditioning, and an initial noise, with absolutely no text prompt. The core architecture behind the scene is ___Semantic Context Encoder(SeeCoder)___, substituting the commonly used CLIP-based or LLM-based text encoder.
SeeCoder:
- is reusable
- can be pre-trained in one T2I model and reuse it for another

## 1. Introduction
By far it remains an open question of what is the most convenient way to achieve personalization in image generation. 
Approaches:
- [[DreamBooth]]
	- have shown promising quality by finetuning model weights.
	- (-) finetuning model weights remains resource-costly
- Prompt-engineering
	- (+) improving output quality from almost zero cost
	- (-) searching high quality text prompts is more art than science
- [[ControlNet]]
	- Captions alone may not provide a comprehensive representation of all visual cues, and providing structural guidance does not eliminate this problem
To overcome these challenges, we introduced the novel _Prompt-Free Diffusion_, replacing the regular prompts input with reference images.
_Semantic Context Encoder (SeeCoder)_ can auto-transform pixel-based images with arbitrary resolutions into meaningful visual embeddings. 
Such embeddings can represent:
- low-level information
	- textures
	- effects
	- etc.
- high-level information
	- objects
	- semantics
	- etc.
We then use these visual embeddings as the conditional inputs of T2I model.

>[!note]
>SeeCoder is _reusable_ to most open-sourced T2I models in which one can easily convert the T2I pipeline to our Prompt-Free pipeline without much effort.


## 2. Related Works
- [[T2I Diffusion]]
- [[Exemplar-based Generation models]]

## 3. Method
### 3.1. Prelimiaries
__Diffusion process__ $q(x_{T}|x_{0})$ and $p_{\theta}(x_{T}|x_{0})$ are T-step Markov Chains that gradually degrade $x_0$ to $x_T$ with random noises and recover $x_T$ from these noises:
$$
\begin{align}
& q(x_{T}|x_{0}) = \prod^{T}_{t=1}q(x_{t}|x_{t-1}) = \prod^{T}_{t=1}\mathcal{N}(\sqrt{ 1-\beta_{t} }x_{t-1};\beta_{t}\mathbf{I})  \\
& p_{\theta}(x_{t-1}|x_{t}) = \mathcal{N}(\mu_{\theta}(x_{t}, t), \Sigma_{\theta}(x_{t}, t))
\end{align}
$$
- $\beta_{t}$ : standard deviation of the mixed-in noise at step $t$
- $\mu_{\theta}(x_{t}, t)$, $\Sigma_{\theta}(x_{t}, t)$: network predicted mean and standard deviation under parameter $\theta$ of the denoised signal at step $t$.

The loss function of training is the variational bound for negative log-likelihood:
$$
\begin{align}
& L = \mathbb{E}[-\log p_{\theta}(x_{0})] \leq \mathbb{E}\left[ -\log \frac{{p_{\theta}(x_{0:T})}}{q(x_{1:T}|x_{0})} \right]
\end{align}
$$
[[CLIP]] us a double-encoder network that bridges text-image pairs by minimizing the contrastive loss between their embeddings. CLIP has served as an important prior module for nowadays T2I models such as DALLE-2 and Stable Diffusion. Also, it had been proved by prior works that its well-aligned cross-modal latent space is one of the core reasons for the T2I model's success.
[[Image-Variation]] defines a task that generates images with similar high-level semantics according to another image. Prompt-Free Diffusion is closer to Image-Variation than exemplar-based generation approaches, in which the former finetunes existing T2I models using CLIP image encoder with frozen weights, while the latter proposed domain-specific networks for tasks such as virtual try-on, makeup, etc.

### 3.2. Prompt-Free Diffusion
The text prompts are first tokenized and then encoded into (NxC) context embeddings using CLIP in common T2I. These embeddings are fed into the diffuser's cross-attention layers as inputs. In our Prompt-Free Diffusion, we replace the CLIP text encoder with the newly proposed SeeCoder.
SeeCoder captures visual cues and transforms them into compatible (NxC) embeddings representing: 
- textures
- objects
- backgrounds
- etc.
Prompt-Free Diffusion also doesn't need any image disentanglement as priors because SeeCoder can determine a proper way to encode low- and high-level cues in an unsupervised manner.

![[Screenshot 2023-10-10 at 7.49.50 PM.png]]

![[Screenshot 2023-10-10 at 9.33.33 PM.png]]

### 3.3. Semantic Context Encoder
- Core module in Prompt-Free Diffusion
- Take only image inputs and encode all visual cues into an embedding

CLIP's ViT also encode images but shows limited capacity because:
- unable to take inputs higher than resolution $384^{2}$
- does not capture detail textures, objects, etc.
- trained with contrastive loss making it an indirect way of processing visual cues

SeeCoder can be breakdown into three components:
- _Backbone Encoder_
- _Decoder_
- _Query Transformer_

![[Screenshot 2023-10-10 at 10.04.43 PM.png]]

__Backbone Encoder__ uses [[SWIN-L]] because it transforms arbitrary-resolution images into feature pyramids that better capture visual cues in different scales.

__Decoder__ is a transformer-based network with several convolutions. Specifically speaking, the Decoder takes features from different levels; 
- uses convolutions to equalize channels; 
- concatenates all flattened features; 
- then passes it through 6 multi-head self-attention modules with linear projections and LayerNorms. 
- The final outputs are split and shaped back into 2D
- then sum with lateral-linked input features

__Query Transformer__ finalizes multi-level visual features into a single 1D visual embedding. The network started with 4 freely-learning global queries and 144 local queries. It holds a mixture of cross-attention and self-attention layers one after another. The cross-attentions take local queries as Q and visual features as K and V. The self-attentions use the concatenation of global and local queries as QKV.

Our networks shares similarities with segmentation approaches.

__Training__. We conducted regular training with variation lower-bound loss and required gradient for only SeeCoder's Decoder and Query Transformer. All other weights(i.e. VAE, Diffuser, and SeeCoder's Backbone Encoder) remained frozen.

## 4. Experiments

### 4.1. Performance
![[Screenshot 2023-10-11 at 12.10.37 AM.png]]


![[Screenshot 2023-10-11 at 12.11.45 AM.png]]
Figure 6: Image-Variation comparison between VD, ControlNet, and Prompt-Free Diffusion. Testing samples s are categorized into in-domain and out-of-domain, meaning whether the input can be generated using the pretrained T21 diffuser.

![[Screenshot 2023-10-11 at 12.29.25 AM.png]]


![[Screenshot 2023-10-11 at 12.30.41 AM.png]]


![[Screenshot 2023-10-11 at 12.30.58 AM.png]]