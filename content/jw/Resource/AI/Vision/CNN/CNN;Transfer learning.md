---
tags:
  - AI/Fine-Tuning/Transfer-Learning
---


Previous:
x -> CNN -> softmax(1000)
Transferred:
change softmax(1000) -> softmax(Cat, Dog, ... (anything you want))


- Use [[Pre-trained model]]

Option 1:
- Train only the FC, softmax weights
Option 2:
- Freeze the front convolutions and train the latter convolutions and FCs
Option 3:
- Train the full networks with your data

If you have a lot of data, it will be better to train more parameters


