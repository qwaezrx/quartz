---
tags:
  - Paper_review
  - AI/GAI
---

Paper: [A Comprehensive Survey of AI-Generated Content (AIGC): A History of Generative AI from GAN to ChatGPT](https://arxiv.org/abs/2303.04226)

## Introduction
The core advancements in recent [[AIGC]] compared to prior works are the result of training more sophisticated generative models on larger datasets, using larger foundation model architectures. For example:
- Training data size: [[GPT-2]] WebText(38GB) -> [[GPT-3]] CommonCrawl(570GB after filtering)
- Model size: [[GPT-2]] (1.5B) -> [[GPT-3]] (175B)

Also researchers explored ways to integrate new technologies such as:
- [[RLHF]]: [[GPT-3]] -> [[ChatGPT]]

Meanwhile in computer vision, [[Stable diffusion]], proposed by Stability.AI in 2022, has also shown great success in image generation. Unlike prior methods, generative [[Diffusion Model]]s can help generate high-resolution images by controlling the trade-off between exploration and exploitation.

![[Unimodal_and_Multimodal.png]]

## History of Generative AI

#### GAI in NLP
- `1950s`: [[Hidden Markov Models]], [[Gaussian Mixture Models]]
	- Generated sequential data such as speech and time series.
- [[N-gram language model]]
	- Cannot effectively adapt to long sentences.
- [[RNN]]s
	- Allowing modeling relatively long dependency
- [[LSTM]]s, [[GRU]]s
	- Leveraged gating mechanism to control memory during training.

#### GAI in CV
- Texture synthesis, texture mapping
	- These algorithms were based on hand-designed features, and were limited in their ability to generate complex and diverse images.
- `2014`: [[GAN]]s
- [[VAE]]s
- [[Diffusion Model]]s

The advancement of generative models in various domains have followed different paths, but eventually, the intersection emerged: the [[Transformer]] architecture(2017). Transformer has later been applied in CV and then become the dominant backbone for many generative models in various domains. Such as:
- In NLP:
	- [[BERT]]
	- [[GPT]]
- In CV:
	- [[ViT]]
	- [[SWIN Transformer]]
later takes this concept even further by combining the transformer architecture with visual components, allowing it to be applied to image based downstreams. This intersection also enables models from different domains to be fused together for multimodal tasks. For example:
- [[CLIP]]
	- CLIP is a joint vision-language model that combines the transformer architecture with visual components, allowing it to be trained on a massive amount of text and image data.
	- Can be used as image encoders in multimodal prompting for generation.

In all, transformer based models revolutionized AI generation and led to the possibility of large-scale training.

![[History_of_generative_AI_in_CV_NLP_and_VL.png]]

## Foundations for AIGC

### Foundation Model
- [[Transformer]]
	- Since the introduction of Transformer architecture, it has become the dominant choice in NLP processing due to its parallelism and learning capabilities.
- [[Pre-trained Language Model]]s
	- Autoregressive Language Models([[Decoder Model]])
	- Masked Language Models([[Encoder Model]])

### RLHF
In order to better align [[AIGC]] output with human preferences, [[RLHF]] has been applied to fine-tune models in various applications such as:
- [[Sparrow]]
- [[InstructGPT]]
- [[ChatGPT]]


![[History_of_Generative_AI.png]]

Although [[RLHF]] has shown promising results by incorporating fluency, in this field is impeded by a lack of publicly available benchmarks and implementation resources, leading to a perception that RL is challenging approach for NLP.
To address this issue, an open-source library named [[RL4LMs]] has recently been introduced, consisting of building blocks for fine-tuning and evaluating RL algorithms on LM-based generation.

Beyond human feedback, [[Claude]], favors Constitutional AI, where reward model is learned via RL from AI Feedback([[RLAIF]]).

### Computing
#### Hardware
In past days, training a large [[NN]] using CPUs could take several days or even weeks. However, with the emergence of more powerful computing resources, this process has been accelerated by several orders of magnitude. For instance:
- NVIDIA A100 GPU speed = 7x V100, 11x T4
- [[TPU]]: offer even higher computing performance compared to A100 [[GPU]]s

#### Distributed Training
In traditional [[ML]], training is typically performed on a single machine using a single processor. In [[Distributed Training]], the training workload is split among multiple processors or machines, allowing the model to be trained much faster.

#### Cloud Computing
[[Cloud Computing]] such as [[AWS]] and [[Azure]] providing access to powerful computing resources, deep learning researchers and practitioners could sign up large clusters of GPUs and TPUs as needed.


## Generative AI
### Unimodal Models

#### Generative Language Models
- [[Decoder Model]]s
- [[Encoder Model]]s

![[Instruct_GPT_architecture.png]]

- [[Encoder-Decoder Model]]

#### Vision Generative Models
- [[GAN]]
- [[VAE]]
- [[Flow]]
- [[Diffusion Model]]

![[categories_of_vision_generation_models.png]]

![[Pasted image 20231016204648.png]]

### Multimodal Models
#### Vision Language Generation
The encoder-decoder architecture is often used in Vision Language Generation. The encoder is responsible for learning a contextualized representation of the input data, while the decoder is used to generate raw modalities that reflect cross-model interactions, structure, and coherence in the representation.

- __Vision Language Encoders__
	- `Concatenated Encoders`: A straight-forward solution to this problem is by concatenating the embeddings from single encoders.
		- [[VisualBERT]]
		- [[VL-BERT]]
		- [[UNITER]]
		- Concatenated encoders are all generally based on the same [[BERT]] architecture, and pre-trained with BERT-like tasks.
		- These models always involves a very complicated pre-training process
			- data collection
			- loss design
			- To solve this problem: [[SimVLM]]
	- `Cross-aligned Encoders`
		- To look at pairwise interactions between modalities.
		- Cross-aligned Encoders always use a two-tower structure.
		- [[LXMERT]]
		- [[ViLBERT]]
		- [[CLIP]]

![[Pasted image 20231016205142.png]]


- __Vision Language Decoders__
	- `To-Text Decoders`
		- `Jointly-trained Models`: refer to decoders that require complete cross modal training when decoding representation.
			- T2T generation typically lies in aligning the two modalities during pre-training. As a result, the model requires a stronger encoder rather than a decoder.
			- Large encoder, small decoder
			- [[VLP]]
			- [[ALBEF]]
			- [[BLIP]]
		- `Frozen Models`: freeze the LLM and train an image encoder only.
			- The produced image representations will be embedded in the input embeddings of the language model.
				- This method achieves SotA performance in various zero-shot and few-shot vision language tasks.
			- Frozen vision encoder, frozen language encoder with gated cross-attention-dense layer to fuse the image representation into text representation.
	![[Pasted image 20231016212748.png]]
	- `To-Image Decoders`: Image generation corresponds to the instruction. Commonly used models in image generation also follow an encoder-decoder architecture, where the encoders are more focused on learning language information and the decoders are more focused on restrict image synthesis.
		- `GAN-based Decoders`
			- [[StackGAN]]
			- [[AttnGAN]]
			- [[StyleCLIP]]
		- `Diffusion-based Decoders`
			- [[GLIDE]]
			- [[Imagen]]
			- [[DALL-E-2]]![[Pasted image 20231016224931.png]]
			- Diffusion models are commonly trained on larger dataset with much more parameters
			- There are also works that use [[VAE]] as the decoder.
				- [[DALL-E]]
#### Text Audio Generation
Most models in this field focus on either synthesis tasks such as:
- speech synthesis
- recognition tasks
	- automatic speech recognition
Text audio generation is a distinct task that involves creating novel audio or text using multimodal models.

- [[AdaSpeech]]

#### Text-Music Generation

- [[JTAV]]

#### Text Graph Generation
Text is vague as it carries various redundant information and is also weakly organized in logic.
Knowledge Graph([[Knowledge Graph]]) is structural meaning representation which reflects relationships among semantic internal states as graph structure in a language processing system.

- It can convert natural language text to a logical form, mostly abstract meaning representation([[AMR]])
	- emphasizes on providing machine interpretable representations rather than constructing a semantic network.

`KG-to-text`: aims to generate fluent and logically-coherent text based on already constructed KG.
- [[GTR-LSTM]]
- [[DUALENC]]

`text-to-KQ`: treat text-to-KG construction as a process of knowledge graph completion([[KGC]])
- [[KG-BERT]]

`Semantic Parsing`
- [[MoMu]]
![[Pasted image 20231017000656.png]]
## Applications

![[GAI_applications.png]]
## Reference

![[History_of_Generative_AI_from_GAN_to_ChatGPT.pdf]]


## See More
- [History of Generative AI(Medium)](https://medium.com/artificialis/history-of-generative-ai-paper-explained-6a0edda1b909)
