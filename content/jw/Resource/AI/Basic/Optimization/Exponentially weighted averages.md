

For example in temperature in days:
$V_{t} = \beta V_{t-1} + (1-\beta)\theta_{t}$

$\beta = 0.9 : \approx \text{10 days temperature}$ 
$\beta = 0.98 : \approx \text{50 days temperature}$ 

$V_{100} = 0.1\theta_{100} + 0.1 \times 0.9 \theta_{99} + 0.1 \times (0.9)^{2} \theta_{98} + 0.1 \times (0.9)^{3} \theta_{97} \dots$


- Usually perform better performance
- Requires more memory usage
- Computation is more expensive

## Implementing exponentially weighted averages
$$
\begin{align}
& V_{0} := 0 \\
& V_{1} = \beta V + (1-\beta)\theta_{1} \\
& V_{2} = \beta V + (1-\beta)\theta_{2} \\
& V_{3} = \beta V + (1-\beta)\theta_{3} \\
& \dots
\end{align}
$$

## Bias correction in exponentially weighted averages

Initial part of exponentially weighted averages are not useful if $\beta$ is too small.

Instead of taking $V_t$, use $\frac{V_{t}}{1-\beta^{t}}$ 

