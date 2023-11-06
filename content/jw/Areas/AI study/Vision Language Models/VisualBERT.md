---
tags:
  - AI
---

VisualBERT leverages [[BERT]] as text encoder, [[CNN]] as image encoder.
The embeddings from the image encoder will be directly incorporated into BERT input embeddings, allowing the model to implicitly learn the aligned joint using two visually-grounded language model objectives:
- masked language modeling with image
- sentence image prediction

![[Pasted image 20231016205645.png]]


## Reference
- https://arxiv.org/pdf/2303.04226.pdf