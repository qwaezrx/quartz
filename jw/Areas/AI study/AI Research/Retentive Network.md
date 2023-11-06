---
tags:
  - Paper_review
---

__Original Paper__: https://arxiv.org/abs/2307.08621


## Retentive Network

Foundation architecture for [[LLM]]s, simultaneously achieving:
- training parallelism
- low-cost inference
- good performance

Recurrence + Attention


![[Screenshot 2023-09-18 at 8.51.51 AM.png]]

Similar to [[Linear Transformer]], [[RWKV]]

Transformers can't be written in recurrent fashion because of the softmax.


![[Screenshot 2023-09-18 at 9.27.29 AM.png]]



![[Screenshot 2023-09-18 at 9.34.06 AM.png]]



![[Screenshot 2023-09-18 at 9.37.08 AM.png]]




