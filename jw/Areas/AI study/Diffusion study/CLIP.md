---
tags:
  - AI
author: OpenAI
aliases:
  - Contrastive Language-Image Pre-training
---


>CLIP is a joint vision-language model that combines the transformer architecture with visual components, allowing it to be trained on a massive amount of text and image data.

- Uses dot product as the cross layer, which is more efficient than the transformer encoder, enabling efficient large-scale downstream training. 

## Approach

![[Pasted image 20231017064417.png]]


## CLIP Models
- [[OpenCLIP]] (OpenAI, Nov2022, 354M)
- [[ClipText]] (OpenAI, 63M)


## Training CLIP Models

CLIP is a combination of an image encoder and a text encoder. Its training process can be simplified to thinking of taking an image and its caption. We encode them both with the image and text encoders respectively.

![[Pasted image 20230916013336.png]]

We then compare the resulting embeddings using cosine similarity. When we begin the training process, the similarity will be low, even if the text describes the image correctly.

![[Pasted image 20230916013747.png]]

We update the two models so that the next time we embed them, the resulting embeddings are similar.

![[Pasted image 20230916013837.png]]

The training process also needs to include __negative examples__ of images and captions that don't match, and the model needs to assign them low similarity scores.


## See More
- https://github.com/openai/CLIP
- [Learning Transferable Visual Models From Natural Language Supervision(arXiv)](https://arxiv.org/pdf/2103.00020.pdf)