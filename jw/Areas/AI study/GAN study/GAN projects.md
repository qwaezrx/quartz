---
tags:
  - AI/GAI/CV/GAN
---


**Generative Adversarial Networks : Paper Review** ([Github](https://github.com/happy-jihye/GAN-Papers))

## **GAN Basics**

- [[GAN]]: [Generative Adversarial Networks](https://happy-jihye.github.io/gan/gan-1/) (NIPS 2014) : [arxiv](https://arxiv.org/abs/1406.2661), [review](https://happy-jihye.github.io/gan/gan-1/) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/happy-jihye/GAN/blob/main/gan/gan.ipynb)
    
- [[DCGAN]]: [Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks](https://happy-jihye.github.io/gan/gan-2/) (ICLR 2016) : [arxiv](https://arxiv.org/abs/1511.06434), [review](https://happy-jihye.github.io/gan/gan-2/)
    

## **Conditional GAN**

- [`CGAN`: Conditional Generative Adversarial Nets](https://happy-jihye.github.io/gan/gan-3/) (2014) : [arxiv](https://arxiv.org/abs/1411.1784), [review](https://happy-jihye.github.io/gan/gan-3/)
    
- [`ACGAN`: Conditional Image Synthesis With Auxiliary Classifier GANs](https://happy-jihye.github.io/gan/gan-13/) (ICML 2017) : [arxiv](https://arxiv.org/abs/1610.09585), [review](https://happy-jihye.github.io/gan/gan-13/)
    
- **Supervised Approach**
    
    - `Pix2Pix`: [Image-to-Image Translation with Conditional Adversarial Networks](https://happy-jihye.github.io/gan/gan-8/) (CVPR 2017) : [arxiv](https://arxiv.org/abs/1611.07004), [review](https://happy-jihye.github.io/gan/gan-8/)
    - `GAN Dissection`: [Visualizing and Understanding Generative Adversarial Networks](https://happy-jihye.github.io/gan/gan-25/#111-gan-dissection) (ICLR 2019) : [arxiv](https://arxiv.org/abs/1811.10597), [review](https://happy-jihye.github.io/gan/gan-25/#111-gan-dissection, [project page](https://gandissect.csail.mit.edu/)
    - [`GauGAN`: Semantic Image Synthesis with Spatially Adaptive Normalization (SPADE)](https://happy-jihye.github.io/gan/gan-9/) (CVPR 2019) : [arxiv](https://arxiv.org/abs/1903.07291), [review](https://happy-jihye.github.io/gan/gan-9/)
- **Unsupervised Approach**
    
    - [`CycleGAN`: Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks](https://happy-jihye.github.io/gan/gan-10/) (ICCV 2017) : [arxiv](https://arxiv.org/abs/1703.10593), [review](https://happy-jihye.github.io/gan/gan-10/)
    - `FUNIT`: Few-Shot Unsupervised Image-to-Image Translation (ICCV 2019) : [arxiv](https://arxiv.org/abs/1905.01723)
    - `COCO-FUNIT`: Few-Shot Unsupervised Image Translation with a Content Conditioned Style Encoder (ECCV 2020) : [arxiv](https://nvlabs.github.io/COCO-FUNIT/)
    - [`HiGAN`: Semantic Hierarchy Emerges in Deep Generative Representations for Scene Synthesis](https://happy-jihye.github.io/gan/gan-25/#121-higan) (IJCV 2020) : [arxiv](https://arxiv.org/abs/1911.09267), [review](https://happy-jihye.github.io/gan/gan-25/#121-higan), [project page](https://genforce.github.io/higan/)
- **Multi Domain**
    
    - `BicycleGAN`: Toward Multimodal Image-to-Image Translation (NIPS 2017) : [arxiv](https://arxiv.org/abs/1711.11586)
    - [`StarGAN`: Unified Generative Adversarial Networks for Multi-Domain Image-to-Image Translation](https://happy-jihye.github.io/gan/gan-12/) (CVPR 2018) : [arxiv](https://arxiv.org/abs/1711.09020), [review](https://happy-jihye.github.io/gan/gan-12/)
        - `StarGAN v2`: Diversity Image Synthesis for Multiple Domains (CVPR 2020) : [arxiv](https://arxiv.org/abs/1912.01865)
    - [`MUNIT` : Multi-Modal Unsupervised Image-to-Image Translation](https://happy-jihye.github.io/gan/gan-14/) (ECCV 2018) : [arxiv](https://arxiv.org/abs/1804.04732), [review](https://happy-jihye.github.io/gan/gan-14/)

## **GAN Architecture**

- [[PGGAN]]: [Progressive Growing of GANs for Improved Quality, Stability, and Variation](https://happy-jihye.github.io/gan/gan-5/) (ICLR 2018) : [arxiv](https://arxiv.org/abs/1710.10196), [review](https://happy-jihye.github.io/gan/gan-5/)
    
- [[StyleGAN]]: [A Style-Based Generator Architecture for Generative Adversarial Networks](https://happy-jihye.github.io/gan/gan-6/) (CVPR 2019) : [arxiv](https://arxiv.org/abs/1812.04948), [review](https://happy-jihye.github.io/gan/gan-6/)
    
	- __StyleGAN v2__: [Analyzing and Improving the Image Quality of StyleGAN](https://happy-jihye.github.io/gan/gan-7/) (2020) : [arxiv](https://arxiv.org/abs/1912.04958), [review](https://happy-jihye.github.io/gan/gan-7/)
        
	- __StyleGAN-ADA__: Training Generative Adversarial Networks with Limited Data (NeurlPS 2020) : [arxiv](https://arxiv.org/abs/2006.06676) : review [#01](https://happy-jihye.github.io/gan/gan-19/), [#02](https://happy-jihye.github.io/gan/gan-20/) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/happy-jihye/GAN-Papers/blob/main/gan/stylegan2-ada.ipynb)
        
	- __[[StyleGAN3]]__: [Alias-Free Generative Adversarial Networks](https://happy-jihye.github.io/gan/gan-33/) (NeurIPS 2021) : [arxiv](https://arxiv.org/abs/2106.12423), [code](https://github.com/NVlabs/stylegan3), [project](https://nvlabs.github.io/alias-free-gan/), [review](https://happy-jihye.github.io/gan/gan-33/)
        
		- __StyleGAN3-Editing__: Third Time’s the Charm? Image and Video Editing with StyleGAN3](https://happy-jihye.github.io/gan/gan-35/) (arxiv 2022) : [arxiv](https://arxiv.org/abs/2201.13433), [project](https://yuval-alaluf.github.io/stylegan3-editing/), [code](https://github.com/yuval-alaluf/stylegan3-editing), [review](https://happy-jihye.github.io/gan/gan-35/)

- __BigGAN__: Large Scale GAN Training for High Fidelity Natural Image Synthesis (2019) : [arxiv](https://arxiv.org/abs/1809.11096)
    

## **Text-to-Image**

- [Generative Adversarial Text to Image Synthesis](https://happy-jihye.github.io/gan/gan-4/) (ICML 2016) : [arxiv](https://arxiv.org/abs/1605.05396), [review](https://happy-jihye.github.io/gan/gan-4/)
    
- `TediGAN`: Text-Guided Diverse Face Image Generation and Manipulation (CVPR 2021) : [arxiv](https://arxiv.org/abs/2012.03308), [code](https://github.com/IIGROUP/TediGAN)
    
- [`StyleCLIP`: Text-Driven Manipulation of StyleGAN Imagery](https://happy-jihye.github.io/gan/gan-15/) (arXiv 2021) : [arxiv](https://arxiv.org/abs/2103.17249), [review](https://happy-jihye.github.io/gan/gan-15/)
    
- `DALLE`: Zero-Shot Text-to-Image Generation (ICML 2021) : [arxiv](https://arxiv.org/abs/2102.12092), [project page](https://openai.com/blog/dall-e/)
- Paint by Word (2021) : [arxiv](https://arxiv.org/abs/2103.10951)

**Improved Training Techniques**

- [`SS-GAN`: Self-Supervised GANs via Auxiliary Rotation Loss](https://happy-jihye.github.io/gan/gan-16/) (CVPR 2019) : [paper](https://openaccess.thecvf.com/content_CVPR_2019/papers/Chen_Self-Supervised_GANs_via_Auxiliary_Rotation_Loss_CVPR_2019_paper.pdf), [review](https://happy-jihye.github.io/gan/gan-16/)
    
- [`CR-GAN`: Consistency Regularization for Generative Adversarial Networks](https://happy-jihye.github.io/gan/gan-17/) (ICLR 2020) : [arxiv](https://arxiv.org/abs/1910.12027), [review](https://happy-jihye.github.io/gan/gan-17/)
    
- [`ICR-GAN`: Improved Consistency Regularization for GANs](https://happy-jihye.github.io/gan/gan-18/) (AAAI 2021) : [arxiv](https://arxiv.org/abs/2002.04724), [review](https://happy-jihye.github.io/gan/gan-18/)
    

## **GAN Inversion**

1. **Latent Optimization**
    - [`Image2stylegan`: How to embed images into the stylegan latent space?](https://happy-jihye.github.io/gan/gan-23/) (ICCV 2019) : [arxiv](https://arxiv.org/abs/1904.03189), [review](https://happy-jihye.github.io/gan/gan-23/)
    - `Image2stylegan++`: How to edit the embedded images? (CVPR 2020) : [arxiv](https://arxiv.org/abs/1911.11544)
    - [`StyleFlow`: Attribute-conditioned Exploration of StyleGAN-Generated Images using Conditional Continuous Normalizing Flows](https://happy-jihye.github.io/gan/gan-25/#123-styleflow) (ACM TOG 2021) : [arxiv](https://arxiv.org/abs/2008.02401), [review](https://happy-jihye.github.io/gan/gan-25/#123-styleflow), [project page](https://rameenabdal.github.io/StyleFlow/)
    - [`BDInvert`: GAN Inversion for Out-of-Range Images with Geometric Transformations](https://happy-jihye.github.io/gan/gan-32/) (ICCV 2021) : [arxiv](https://arxiv.org/abs/2108.08998), [review](https://happy-jihye.github.io/gan/gan-32), [code](https://github.com/kkang831/BDInvert_Release)
2. **Encoder**
    - `ALAE`: Adversarial latent autoencoders (CVPR 2020) : [arxiv](https://arxiv.org/abs/2004.04467), [code](https://github.com/podgorskiy/ALAE)
    - [`pSp`: Encoding in Style: a StyleGAN Encoder for Image-to-Image Translation](https://happy-jihye.github.io/gan/gan-23/#3-psp--pixel2style2pixel) (CVPR 2021) : [arxiv](https://arxiv.org/abs/2008.00951), [review](https://happy-jihye.github.io/gan/gan-23/#3-psp--pixel2style2pixel), [code](https://happy-jihye.github.io/gan/gan-23/)
3. **Hybrid approach**
    - `stylegan-encoder` : [code](https://github.com/pbaylies/stylegan-encoder)
    - [`IdInvert` : In-Domain GAN Inversion for Real Image Editing](https://happy-jihye.github.io/gan/gan-23/#2-idinvert) (ECCV 2020) : [arxiv](https://arxiv.org/abs/2004.00049), [review](https://happy-jihye.github.io/gan/gan-23/#2-idinvert), [code](https://github.com/happy-jihye/GAN/tree/main/In-Domain-GAN)

## **Disentangled Manipulation**

- [`GANSpace`: Discovering Interpretable GAN Controls](https://happy-jihye.github.io/gan/gan-25/#22-ganspace) (NeurIPS 2020) : [arxiv](https://arxiv.org/abs/2004.02546), [review](https://happy-jihye.github.io/gan/gan-25/#22-ganspace), [code](https://github.com/harskish/ganspace)
- `GAN-Latent-Discovery`: Unsupervised Discovery of Interpretable Directions in the GAN Latent Space (2020) : [arxiv](https://arxiv.org/abs/2002.03754), [code](https://github.com/anvoynov/GANLatentDiscovery)
- `Editing in style`: Uncovering the Local Semantics of GANs (CVPR 2020) : [arxiv](https://arxiv.org/abs/2004.14367), [code](https://github.com/IVRL/GANLocalEditing)
- [`HiGAN`: Semantic Hierarchy Emerges in Deep Generative Representations for Scene Synthesis](https://happy-jihye.github.io/gan/gan-25/#121-higan) (IJCV 2020) : [arxiv](https://arxiv.org/abs/1911.09267), [review](https://happy-jihye.github.io/gan/gan-25/#121-higan), [project page](https://genforce.github.io/higan/)
- [`InterFaceGAN`: Interpreting the Latent Space of GANs for Semantic Face Editing](https://happy-jihye.github.io/gan/gan-25/#122-interfacegan) (CVPR 2020) : [arxiv](https://arxiv.org/abs/1907.10786), [review](https://happy-jihye.github.io/gan/gan-25/#122-interfacegan), [project page](https://genforce.github.io/interfacegan/)
- [`CDDFM3D`: Cross-Domain and Disentangled Face Manipulation with 3D Guidance](https://happy-jihye.github.io/gan/gan-24/) (2021) : [arxiv](https://arxiv.org/abs/2104.11228), [review](https://happy-jihye.github.io/gan/gan-24/), [code](https://github.com/cassiePython/cddfm3d)
- `GHFeat`: Generative Hierarchical Features from Synthesizing Images (CVPR 2021) : [arxiv](https://arxiv.org/abs/2007.10379), [project page](https://genforce.github.io/ghfeat/)
- `StyleSpace`: StyleSpace Analysis: Disentangled Controls for StyleGAN Image Generation (2021) : [arxiv](https://arxiv.org/abs/2011.12799), [code](https://github.com/xrenaa/StyleSpace-pytorch), [code2](https://github.com/happy-jihye/GAN/tree/main/StyleSpace)
- [`StyleFlow`: Attribute-conditioned Exploration of StyleGAN-Generated Images using Conditional Continuous Normalizing Flows](https://happy-jihye.github.io/gan/gan-25/#123-styleflow) (ACM TOG 2021) : [arxiv](https://arxiv.org/abs/2008.02401), [review](https://happy-jihye.github.io/gan/gan-25/#123-styleflow), [project page](https://rameenabdal.github.io/StyleFlow/)
- [`Hessian Penalty`: A weak prior for unsupervised disentanglement](https://happy-jihye.github.io/gan/gan-25/#23-hessian-penalty) (ECCV 2020) : [arxiv](https://arxiv.org/abs/2008.10599), [review](https://happy-jihye.github.io/gan/gan-25/#23-hessian-penalty), [project page](https://www.wpeebles.com/hessian-penalty)

## **Image Editing**

- [`StyleCLIP`: Text-Driven Manipulation of StyleGAN Imagery](https://happy-jihye.github.io/gan/gan-15/) (arXiv 2021) : [arxiv](https://arxiv.org/abs/2103.17249), [review](https://happy-jihye.github.io/gan/gan-15/), [code](https://github.com/orpatashnik/StyleCLIP)
- [`sefa`: Closed-Form Factorization of Latent Semantics in GANs](https://happy-jihye.github.io/gan/gan-25/#21-sefa) (CVPR 2021) : [arxiv](https://arxiv.org/abs/2007.06600), [review](https://happy-jihye.github.io/gan/gan-25/#21-sefa), [code](https://github.com/happy-jihye/GAN/tree/main/SEFA)
- [`EigenGAN`: Layer-Wise Eigen-Learning for GANs](https://happy-jihye.github.io/gan/gan-25/#24-eigengan) : [arxiv](https://arxiv.org/abs/2104.12476), [review](https://happy-jihye.github.io/gan/gan-25/#24-eigengan), [code](https://github.com/bryandlee/eigengan-pytorch)
- `StyleMapGAN`: Exploiting Spatial Dimensions of Latent in GAN for Real-time Image Editing (CVPR 2021) : [arxiv](https://arxiv.org/abs/2104.14754), [code](https://github.com/naver-ai/StyleMapGAN)
- `SEAN`: Image Synthesis with Semantic Region-Adaptive Normalization (CVPR 2020) : [arxiv](https://arxiv.org/abs/1911.12861), [code](https://github.com/ZPdesu/SEAN)
- [`CDDFM3D`: Cross-Domain and Disentangled Face Manipulation with 3D Guidance](https://happy-jihye.github.io/gan/gan-24/) (2021) : [arxiv](https://arxiv.org/abs/2104.11228), [review](https://happy-jihye.github.io/gan/gan-24/), [code](https://github.com/cassiePython/cddfm3d)
- [`MocoGAN-HD`: A Good Image Generator Is What You Need for High-Resolution Video Synthesis](https://happy-jihye.github.io/gan/gan-27/) (ICLR 2021) : [arxiv](https://arxiv.org/abs/2104.15069), [review](https://happy-jihye.github.io/gan/gan-27/), [code](https://github.com/snap-research/MoCoGAN-HD), [project](https://bluer555.github.io/MoCoGAN-HD/)

## **Webtoon/Anime GAN & Image Blending**

- [`Cartoon-StyleGAN`: Fine-tuning StyleGAN2 for Cartoon Face Generation](https://happy-jihye.github.io/gan/(https://happy-jihye.github.io/gan/gan-21/)) (arxiv 2021) : [arxiv](https://arxiv.org/abs/2106.12445), [review](https://happy-jihye.github.io/gan/gan-21/), [code](https://github.com/happy-jihye/Cartoon-StyleGAN)
- `BlendGAN`: Implicitly GAN Blending for Arbitrary Stylized Face Generation (NeurIPS 2021) : [arxiv](https://arxiv.org/abs/2110.11728), [project](https://onion-liu.github.io/BlendGAN/), [code](https://github.com/onion-liu/BlendGAN)
- `HifiFace`: 3D Shape and Semantic Prior Guided High Fidelity Face Swapping (IJCAI 2021) : [arxiv](https://arxiv.org/abs/2106.09965)
- `AnimeGAN`: A Novel Lightweight GAN for Photo Animation (ISICA 2019)
    - `AnimeGANv2` (2021) : [project](https://tachibanayoshino.github.io/AnimeGANv2/), [code](https://github.com/bryandlee/animegan2-pytorch)
- `StyleGAN of All Trades`: Image Manipulation with Only Pretrained StyleGAN (arxiv 2021) : [arxiv](https://arxiv.org/abs/2111.01619), [code](https://github.com/mchong6/SOAT)

## **Super Resolution**

- `BSRGAN`: Designing a Practical Degradation Model for Deep Blind Image Super-Resolution (ICCV 2021) : [arxiv](https://arxiv.org/abs/2103.14006), [code](https://github.com/cszn/BSRGAN)
- `Real-ESRGAN`: Training Real-World Blind Super-Resolution with Pure Synthetic Data (ICCVW 2021): [arxiv](https://arxiv.org/abs/2107.10833), [code](https://github.com/xinntao/Real-ESRGAN)

## **Sketch based Generation**

- [`GANSketching` : Sketch Your Own GAN](https://happy-jihye.github.io/gan/gan-36/) (ICCV 2021) : [arxiv](https://arxiv.org/abs/2108.02774), [project](https://peterwang512.github.io/GANSketching/), [code](https://github.com/PeterWang512/GANSketching), [review](https://happy-jihye.github.io/gan/gan-36/)

## **3D GAN & Rendering**

- `HoloGAN`: Unsupervised learning of 3D representations from natural images (ICCV 2019): [paper](https://arxiv.org/abs/1904.01326), [code](https://github.com/thunguyenphuoc/HoloGAN)
- [`CDDFM3D`: Cross-Domain and Disentangled Face Manipulation with 3D Guidance](https://happy-jihye.github.io/gan/gan-24/) (2021) : [arxiv](https://arxiv.org/abs/2104.11228), [review](https://happy-jihye.github.io/gan/gan-24/), [project](https://cassiepython.github.io/cddfm3d/index), [code](https://github.com/cassiePython/cddfm3d)
- `SofGAN`: A Portrait Image Generator with Dynamic Styling (arxiv 2021): [arxiv](https://arxiv.org/abs/2007.03780), [project](https://apchenstu.github.io/sofgan/), [code](https://github.com/apchenstu/sofgan)
- `pi-GAN`: Periodic Implicit Generative Adversarial Networks for 3D-Aware Image Synthesis (CVPR 2021): [paper](https://arxiv.org/pdf/2012.00926.pdf), [project](https://marcoamonteiro.github.io/pi-GAN-website/), [code](https://marcoamonteiro.github.io/pi-GAN-website/)
- `StyleGANRender`: Image GANs meet Differentiable Rendering for Inverse Graphics and Interpretable 3D Neural Rendering (ICLR 2021) : [arxiv](https://arxiv.org/abs/2010.09125), [project page](https://nv-tlabs.github.io/GANverse3D/)
- `StyleNeRF`: A Style-based 3D Aware Generator for High-resolution Image Synthesis (ICLR 2022): [paper](https://openreview.net/forum?id=iUuzzTMUw9K)
    - `NeRF`: Representing Scenes as Neural Radiance Fields for View Synthesis (ECCV 2020) : [arxiv](https://arxiv.org/abs/2003.08934), [project](https://www.matthewtancik.com/nerf)
- `CIPS-3D`: A 3D-Aware Generator of GANs Based on Conditionally-Independent Pixel Synthesis (arxiv 2021): [arxiv](https://arxiv.org/abs/2110.09788), [code](https://github.com/PeterouZh/CIPS-3D)

---

😊 Talking Head : [Paper list](https://stream-chameleon-81c.notion.site/1fa3a78b6c54415784175c50eddfe3cc?v=ddc7ecf4fb0f484d8a98cb7da3fd1ea5)[Permalink](https://happy-jihye.github.io/gan/#-talking-head--paper-list "Permalink")

- [`MocoGAN-HD`: A Good Image Generator Is What You Need for High-Resolution Video Synthesis](https://happy-jihye.github.io/gan/gan-27/) (ICLR 2021) : [arxiv](https://arxiv.org/abs/2104.15069), [review](https://happy-jihye.github.io/gan/gan-27/), [code](https://github.com/snap-research/MoCoGAN-HD), [project](https://bluer555.github.io/MoCoGAN-HD/)

## **Landmark-based Model**

- [Few-Shot Adversarial Learning of Realistic Neural Talking Head Models](https://happy-jihye.github.io/gan/gan-22/) (ICCV 2019) : [arxiv](https://arxiv.org/abs/1905.08233), [review](https://happy-jihye.github.io/gan/gan-22/)
- `LPD`: Neural Head Reenactment with Latent Pose Descriptors (CVPR 2020) : [Paper](https://arxiv.org/abs/2004.12000), [project](https://saic-violet.github.io/latent-pose-reenactment/), [code](https://github.com/shrubb/latent-pose-reenactment)

## **Warping-based Model**

- `X2Face`: A network for controlling face generation by using images, audio, and pose codes (ECCV 2018) : [arxiv](https://arxiv.org/abs/1807.10550), [project](https://www.robots.ox.ac.uk/~vgg/research/unsup_learn_watch_faces/x2face.html)
- `Monkey-Net`: Animating Arbitrary Objects via Deep Motion Transfer (CVPR 2019) : [arxiv](https://arxiv.org/abs/1812.08861), [project](http://www.stulyakov.com/papers/monkey-net.html), [code](https://github.com/AliaksandrSiarohin/monkey-net)
- `FOMM`: First Order Motion Model for Image Animation (NeurIPS 2019) : [arxiv](https://arxiv.org/abs/2003.00196), [code](https://github.com/AliaksandrSiarohin/first-order-model)
- `face vid2vid`: One-Shot Free-View Neural Talking-Head Synthesis for Video Conferencing (CVPR 2021): [arxiv](https://arxiv.org/abs/2011.15126), [project](https://nvlabs.github.io/face-vid2vid/)
- `articulated animation`: Motion Representations for Articulated Animation (CVPR 2021) : [arxiv](https://arxiv.org/abs/2104.11280), [code](https://github.com/snap-research/articulated-animation), [project](https://snap-research.github.io/articulated-animation/)