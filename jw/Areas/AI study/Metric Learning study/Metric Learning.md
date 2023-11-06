#Metric_Learning 

Paper: [Deep Metric Learning: A Survey](https://www.mdpi.com/2073-8994/11/9/1066)


## Introduction
_Metric Learning_은 input data간 거리를 학습하는 것. 즉, input data 간의 거리/유사도를 측정할 수 있다면, 이를 맞추어나가는 과정을 통해 input data를 설명하는 [[Embedding]]을 학습하는 것.


## Metric Learning vs. Classification
- _Classification_: input data $x$는 $y$이다
- _Metric Learning_: input data $x_1$ 은  $x_2$ 와는 비슷하고 $x_3$ 과는 다르다


## Metric Learning
### 1. Informative Input Samples
positive "or" negative sample을 뽑는 과정. 유사도는 데이터 하나를 기준으로 두고 정하게 되는데 이를 anchor라고 한다.

![[Negative Mining.png]]
<caption>Negative Mining</caption>

### 2. Structure of the Network Model
Model network는 크게 [[Siamese network]]와 [[Triplet Network]]로 나뉜다.
- Triplet Network: Triplet Mining (anchor/positive/negative)
- Siamese Network: anchor/{positive, negative}

Metric Learning 특징 상, input data pair가 들어가게 되고, 이 때 모델은 weight sharing을 통해 parameter의 갯수를 줄이고, 성능 향상에 기여한다.
![[Siamese_network_and_Triplet_network.png | "Siamese Network & Triplet Network"]]

### 3. Metric Loss Function
- [[Contrastive Loss]]
- [[Triplet Loss]]
- [[Angular Loss]]

