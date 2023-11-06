---
tags:
  - AI/CV
---

## ResNets

## Residual block

![[IMG_1BC66CA0FEFE-1.jpeg]]

$$
a^{[l+2]} = g(z^{[l+2]} + a^{[l]})
$$

- Helps with the [[Vanishing, exploding gradients]]
- Allows you to train much deeper NNs.

![[IMG_FA6A6CDDD343-1.jpeg]]


## Why ResNet work so well?

$$
a^{[l+2]} = g(z^{[l+2]} + a^{[l]}) = g(W^{[l+2]}a^{[l+1]} + b^{[l+2]} + a^{[l]})
$$

if $(W^{[l+2]}=0, b^{[l+2]}=0) \implies (a^{[l+2]} =a^{[l]})$

![[IMG_B0082D569C4E-1.jpeg]]


