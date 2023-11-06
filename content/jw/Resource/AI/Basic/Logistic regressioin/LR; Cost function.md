
[[Cost function]] for [[Logistic regression]]

$$
\begin{align}
& \hat{y} = \sigma(w^{T}x + b), \text{where } \sigma(z) = \frac{1}{1 + e^{-z}}  \\
& \text{Given } \{ (x^{(1)}, y^{(1)}), \dots , (x^{(m)}, y^{(m)}) \}, \text{want } \hat{y}^{(i)} \approx y^{(i)}  \\
& \text{Loss(error) function}: L(\hat{y}, y)
\end{align}
$$


> [!note]
> In [[Logistic regression]], $\frac{1}{2}(\hat{y} - y)^{2}$ is not used well because [[Gradient descent]] don't work well


$$
J(\theta) = -\dfrac{1}{m}\sum_{i=1}^m \left[ y^{(i)} \log{\sigma(x^{(i)}, \theta)} + (1-y^{(i)})\log{(1-\sigma(x^{(i)}, \theta))} \right]
$$


## Math Derivation
$$
\begin{align}

& \hat{y} = p(y = 1|x)\\
& \text{If } y = 1: \quad p(y|x) = \hat{y} \\
& \text{If } y = 0: \quad p(y|x) = 1-\hat{y}  \\
\\
& p(y|x) = \hat{y}^{y} (1-\hat{y})^{(1-y)}
\end{align}
$$

$$
P(y | x^{(i)}, \theta) = h(x^{(i)}, \theta)^{y^{(i)}}( 1- h(x^{(i)}, \theta))^{(1 - {y^{(i)}})}
$$
We should use second one for cost function
Now we want to find a way to model the entire data set and not just one example. To do so, we will define the likelihood as follows:
$$
L(\theta) = \Pi_{i=1}^mP(y|x^{(i)}, \theta)
$$
>[!note]
>If we mess up the classification for one example, we end up messing up the overall likelihood score, which is exactly what we intended.

One issue is that as $m$ gets larger, $L(\theta)$ goes close to zero.

using $\log$, we can rewrite the equation as follows:
$$
\max_{h(x^{(i)}, \theta)}\log{L(\theta)} = \sum_{i=1}^m\log{P(y|x^{(i)}, \theta)}
$$
$$
= \sum_{i=1}^m\log{h(x^{(i)}, \theta)^{y^{(i)}}( 1- h(x^{(i)}, \theta))^{(1 - {y^{(i)}})}}
$$
$$
= \sum_{i=1}^m y^{(i)}\log{h(x^{(i)}, \theta)} + (1-y^{(i)})\log{(1-h(x^{(i)}, \theta))}
$$
Hence, we now divide by $m$, because we want want to see the average cost.
$$\dfrac{1}{m}\sum_{i=1}^m y^{(i)}\log{h(x^{(i)}, \theta)} + (1-y^{(i)})\log{(1-h(x^{(i)}, \theta))}$$
Remember that we were maximizing $h(x^{(i)}, \theta)$ in the equation above.
Maximizing the equation is the same as minimizing its negative.

Hence we add a negative sign and we end up minimizing the cost function as follows:
$$
J(\theta) = -\dfrac{1}{m}\sum_{i=1}^m [y^{(i)}\log{h(x^{(i)}, \theta)} + (1-y^{(i)})\log{(1-h(x^{(i)}, \theta))}]
$$
A vectorized implementation is:
$$
h = g(X\theta)$$
$$J(\theta) = \dfrac{1}{m} \cdot (-y^T\log(h) - (1-y^T)\log(1-h))
$$



