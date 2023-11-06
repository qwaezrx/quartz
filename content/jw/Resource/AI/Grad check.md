
_Gradient checking_ is a technique that's helpful in finding bugs in the implementation of [[Neural Network#Back propagation]].

Take $W^{[1]}, b^{[1]}, \dots, W^{[L]}, b^{[L]}$ and reshape(concatenate) into a big vector $\theta$.
$$
\mathcal{J}(W^{[1]}, b^{[1]}, \dots, W^{[L]}, b^{[L]}) = \mathcal{J}(\theta)
$$

Take $dW^{[1]}, db^{[1]}, \dots, dW^{[L]}, db^{[L]}$ and reshape(concatenate) into a big vector $d\theta$.
$$
\mathcal{J}(dW^{[1]}, db^{[1]}, \dots, dW^{[L]}, db^{[L]}) = \mathcal{J}(d\theta)
$$

for each i:
	$$\begin{align} 
 \text{for i } \{\\
& d\theta_{\text{approx}}[i] = \frac{{\mathcal{J}(\theta_{1}, \theta_{2}, \dots, \theta_{i} + \epsilon, \dots) - \mathcal{J}(\theta_{1}, \theta_{2}, \dots, \theta_{i} - \epsilon, \dots)}}{2\epsilon} \\
& \approx d\theta[i] = \frac{\partial\mathcal{J}}{\partial\theta_{i}}  \\ \\

	& \text{Check}  \\
    & \|d\theta_{approx} - d\theta \|_{2} \approx 0  \\
\}
\end{align}$$
	
## Gradient checking implementation notes
- Don't use in training - only to debug (training becomes too slow)
- If algorithm fails grad check, look at components to try to identify bug.
- Remember regularization
- Doesn't work with dropout
- Run at random initialization; perhaps again after some training.

