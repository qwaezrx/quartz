---
tags:
  - AI/Transformer
---


![[Screenshot 2023-09-04 at 4.22.59 AM.png]]


$$
\begin{align} 
&a^{<t>} = ({\overset{\rightarrow}a}^{<t'>}, {\overset{\leftarrow} a}^{<t'>} )\\
& \alpha^{<t, t'>}: \text{amount of "attention"} y^{<t>} \text{should pay to } a^{<t'>} \\
& \alpha^{<t, t'>} = \frac{\exp(e^{<t, t'>})}{\sum^{T_{x}}_{t'=1}\exp(e^{<t, t'>})}  \\
\\
& \sum_{t'=1}^{T_{x}}\alpha^{<t, t'>} = 1  \\
& c^{<t>} = \sum_{t'=1}^{T_{x}}\alpha^{<t, t'>}a^{<t'>}  \\
& c: \text{context}
\end{align}
$$


![[Screenshot 2023-09-04 at 4.45.34 AM.png]]

- It takes quadratic COCO to run this algorithm

- The network learns where to "pay attention" by learning the values $e^{<t, t'>}$, which are computed using a small neural network. We can replace $s^{<t-1>}$ with $s^{<t>}$ as an input to this neural network. This is because $s ^{<t>}$ depends on $\alpha^{<t, t'>}$ which in turn depends on $e^{<t, t'>}$; so at the time we need to evaluate this network, we haven't computed $s ^{<t>}$ yet.


![[Sequential_LSTM_Attention.png]]

![[Pasted image 20230904124225.png]]


## Attention with [[Seq2seq]]

![[Seq2Seq_Attention.png]]


![[IMG_1A1CA6901630-1.jpeg]]


