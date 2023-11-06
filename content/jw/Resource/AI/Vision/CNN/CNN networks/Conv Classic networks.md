---
tags:
  - AI/CV
---

Common classic [[CNN]]s

## [[LeNet-5]]
Goal: recognize handwritten digits

#### Model
- Input(32, 32, 1) 
- Conv2D((5, 5,) stride=1) -> (28, 28, 6)
- AvgPool(filter=2, stride=2) ->(14, 14, 6)
- Conv2D((5, 5,) stride=1) -> (10, 10, 16)
- AvgPool(filter=2, stride=2) ->(5, 5, 16)
- FC(120)
- FC(84)
- softmax(10)

#### LeNet-5 features
- 60K parameters
- $n_{H}, n_{W}$ decrease
- $n_{C}$ increases
- non linearity after pooling

## [[AlexNet]]

#### Model
- Input(227, 227, 3)
- Conv2D((11, 11), stride=4) -> (55, 55, 96)
- MaxPool((3, 3), stride=2) -> (27, 27, 96)
- Same Conv2D((5, 5)) -> (27, 27, 256)
- MaxPool((3, 3), stride=2) -> (13, 13, 256)
- Same Conv2D((3, 3)) -> (13, 13, 384)
- Same Conv2D((3, 3)) -> (13, 13, 384)
- Same Conv2D((3, 3)) -> (13, 13, 256)
- MaxPool((3, 3), stride=2) -> (6, 6, 256)
- FC(9216)
- FC(4096)
- FC(4096)
- Softmax(1000)

#### AlexNet features
- Similar to LeNet but much bigger
- ReLU
- Multiple GPUs when training
- Local Response Normalization (doesn't help much)


## [[VGG-16]]
- Conv = (3, 3) filter, s = 1, same
- Pool = (2, 2), s=2, max

Simple architecture
#### Model
- Input(224, 224, 3)
- 2 * Conv2D64 -> (224, 224, 64)
- Pool -> (112, 112, 64)
- 2 * Conv2D128 -> (112, 112, 128)
- Pool -> (56, 56, 128)
- 3 * Conv2D256 -> (56, 56, 256)
- Pool -> (28, 28, 256)
- 3 * Conv2D512 -> (28, 28, 512)
- Pool -> (14, 14, 512)
- 3 * Conv2D512 -> (14, 14, 512)
- Pool -> (7, 7, 512)
- FC(4096)
- FC(4096)
- Softmax(1000)

#### VGG-16 features
- 138M parameters (large)

