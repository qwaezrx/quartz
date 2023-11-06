---
tags:
  - AI/GAI/CV/GAN
---

WGAN and [[LS-GAN]] aim to regularize the loss function with a Lipschitz regularity condition on the density of real data in order to better generalize and produce realistic new data.

## Wasserstein Distance
Wasserstein Distance is a distance between two probability distributions. Aka. Earth Mover's distance (EM distance).

![[Pasted image 20230916001734.png]]


![[Screenshot 2023-10-15 at 6.32.28 PM.png]]
W-Loss is a simple expression that computes the difference between the expected values of the critics output for the real examples $x$ and its predictions on the fake examples $g(z)$
![[Screenshot 2023-10-15 at 6.36.33 PM.png]]
![[Screenshot 2023-10-15 at 6.38.15 PM.png]]

## See More
- https://keras.io/examples/generative/wgan_gp/

- Wasserstein GAN (Arjovsky, Chintala, and Bottou, 2017): [https://arxiv.org/abs/1701.07875](https://arxiv.org/abs/1701.07875)

- Improved Training of Wasserstein GANs (Gulrajani et al., 2017): [https://arxiv.org/abs/1704.00028](https://arxiv.org/abs/1704.00028 "https://arxiv.org/abs/1704.00028")

- From GAN to WGAN (Weng, 2017): [https://lilianweng.github.io/lil-log/2017/08/20/from-GAN-to-WGAN.html](https://lilianweng.github.io/lil-log/2017/08/20/from-GAN-to-WGAN.html)

