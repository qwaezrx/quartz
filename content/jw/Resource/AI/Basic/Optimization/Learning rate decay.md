
Slowly reducing the learning rate $\alpha$

1 epoch = 1 pass through data


$$
\begin{align}
\alpha = \frac{1}{1 + \text{decayRate} \times \text{epochNumber}} \alpha_{0}
\end{align}
$$


## Other learning rate decay methods
$$
\alpha = 0.95^{\text{epochNumber}} \alpha_{0}
$$
$$
\alpha = \frac{k}{\sqrt{ \text{epochNumber} }} \alpha_{0}
$$
Also can use __manual decay__

