---
tags:
  - AI/Fine-Tuning/PEFT/LoRA
---


1. Freeze most of the original LLM weights
2. Inject 2 rank decomposition matrices
3. Train the weights of the smaller matrices

Steps to update model for inference
1. Matrix multiply the low rank matrices
2. Add to original weights

![[Screenshot 2023-10-10 at 2.54.32 AM.png]]

You can also use [[LoRA]] on other components like the FF layers. But since most of the parameters of [[LLM]]s are in the attention layers, you get the biggest savings in trainable parameters by applying LoRA to these matrices.

![[Screenshot 2023-10-10 at 2.58.03 AM.png]]

![[Screenshot 2023-10-10 at 2.59.08 AM.png]]


![[Screenshot 2023-10-10 at 2.59.47 AM.png]]
- Using rank larger than 8 didn't improve performance.


