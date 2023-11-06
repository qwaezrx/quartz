---
tags:
  - AI/GAI/CV
  - AI/Transformer
---


[Paper](https://arxiv.org/abs/2010.11929)

## Vision Transformer (ViT)
The Vision Transformer (ViT) model was proposed in [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale](https://arxiv.org/abs/2010.11929)
It's the first paper that successfully trains a Transformer encoder on ImageNet, attaining very good results compared to familiar convolutional architectures.

## Abstract
While the [[Transformer]] architecture has become the _de-facto_ standard for NLP tasks, its applications to computer vision remain limited. In vision, attention is either applied in conjunction with convolutional networks, or used to replace certain components of convolutional networks while keeping their overall structure in place. We show that this reliance on CNNs is not necessary and a pure transformer applied directly to sequences of image patches can perform very well on image classification tasks. When pre-trained on large amounts of data and transferred to multiple mid-sized or small image recognition benchmarks (ImageNet, CIFAR-100, VTAB, etc.), ViT attains excellent results compared to state-of-art convolutional networks while requiring substantially fewer computational resources to train.


![[Pasted image 20231010233351.png]]


## See More
- https://huggingface.co/docs/transformers/model_doc/vit