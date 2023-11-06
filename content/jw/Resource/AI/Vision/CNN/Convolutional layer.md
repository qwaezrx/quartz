---
tags:
  - AI/CV
---

[[CNN]]

## Filter 

### Vertical edge detection
$$
\begin{align}
\underset{ n \times n }{ \begin{pmatrix}
3 & 0 & 1 & 2 & 8 & 6 \\
9 & 7 & 5 & 7 & 3 & 8 \\
9 & 7 & 5 & 7 & 9 & 6 \\
0 & 9 & 1 & 3 & 6 & 3 \\
9 & 8 & 6 & 9 & 0 & 8
\end{pmatrix} } * \underset{ f \times f }{ \begin{pmatrix}
1 & 0 & -1 \\
1 & 0 & -1  \\
1 & 0 & -1
\end{pmatrix} } = \mathbb{R^{(n-f+1) \times (n-f+1)}}
\end{align}
$$

### Learning edge detection
You can treat the filter values as trainable parameters

$$
\begin{align}
\underset{ n \times n }{ \begin{pmatrix}
3 & 0 & 1 & 2 & 8 & 6 \\
9 & 7 & 5 & 7 & 3 & 8 \\
9 & 7 & 5 & 7 & 9 & 6 \\
0 & 9 & 1 & 3 & 6 & 3 \\
9 & 8 & 6 & 9 & 0 & 8
\end{pmatrix} } * \underset{ f \times f }{ \begin{pmatrix}
w_{1} & w_{2} & w_{3} \\
w_{4} & w_{5} & w_{6}  \\
w_{7} & w_{8} & w_{9}
\end{pmatrix} } = \mathbb{R^{(n-f+1) \times (n-f+1)}}
\end{align}
$$
## Padding
Padding helps to solve some problems such as:
- Shrinking output problem
- Throwing away the information on the edges

$$
\begin{align}
\underset{ n \times n }{ \begin{pmatrix}
3 & 0 & 1 & 2 & 8 & 6 \\
9 & 7 & 5 & 7 & 3 & 8 \\
9 & 7 & 5 & 7 & 9 & 6 \\
0 & 9 & 1 & 3 & 6 & 3 \\
9 & 8 & 6 & 9 & 0 & 8
\end{pmatrix} } \to \underset{ (n+p) \times (n+p) }{ \begin{pmatrix}
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 3 & 0 & 1 & 2 & 8 & 6 & 0 \\
0 & 9 & 7 & 5 & 7 & 3 & 8 & 0 \\
0 & 9 & 7 & 5 & 7 & 9 & 6 & 0 \\
0 & 0 & 9 & 1 & 3 & 6 & 3 & 0 \\
0 & 9 & 8 & 6 & 9 & 0 & 8  & 0\\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0
\end{pmatrix} } * \underset{ f \times f }{ \begin{pmatrix}
w_{1} & w_{2} & w_{3} \\
w_{4} & w_{5} & w_{6}  \\
w_{7} & w_{8} & w_{9}
\end{pmatrix} } = \mathbb{R^{n \times n}}

\end{align}
$$
## Valid and Same convolutions
### Valid convolution
$n \times n * f \times f \to (n-f+1) \times (n-f + 1)$
### Same convolution
Pad so that the output size is the same as the input size
$p = \frac{{f-1}}{2}$ (f is odd)

>[!note]
>The $f$ (filter) is almost always odd

## Strided convolution

__Convolution size with stride__ 
$$
(n\times n) * (f \times f) \to (\frac{n+2p-f}{s} + 1) \times (\frac{n+2p-f}{s} + 1) 
$$


## Convolutions over RGB image
(height, width, channel) x (f, f, channel)

>[!important]
>Number of _channels_ on the input image and on the _filter_ should be equal.

(h, w, 3) with filters:
* (f, f, 3) -> (h-f, w-f)
* (f, f, 3) -> (h-f, w-f)
-> (h-f, w-f, 2)
$$
\begin{align}
& n_{c}: \text{number of channels} \\
& n'_{c}: \text{number of filters (number of next channel)}  \\ \\

& (h\times w\times n_{c}) * (f \times f \times n_{c}) \to ((h-f+1) \times (w-f+1) \times n_{c}')
\end{align}
$$


## Example of a layer
$$
\begin{align}
& Z^{[l]} = conv(W^{[l]}, A^{[l-1]}) + b  \\
& A^{[l]} = g(Z^{[l]})
\end{align}
$$
### Number of parameters in layer 
10 filters with (3, 3, 3) filter, how many parameters are there in this layer?
- 10 * 3 * 3 * 3 + 10 = 280 parameters

## Convolution notations

$$
\begin{align}
& l \quad \text{convolutional layer number}  \\
& f^{[l]} \quad \text{filter size}  \\
& p^{[l]} \quad \text{padding}  \\
& s^{[l]} \quad \text{stride}  \\
& n^{[l]}_{c} \quad \text{number of filters}  \\
& n^{[l-1]}_{c} \quad \text{number of channels}  \\ \\
& \text{Input size}: (n_{H}^{[l-1]}, n_{W}^{[l-1]}, n_{c}^{[l-1]}) \\
& \text{Output size}: (n_{H}^{[l]}, n_{W}^{[l]}, n_{c}^{[l]}) \\ \\
& n^{[l]}_{H} = \frac{{n^{[l-1]}_{H} + 2p - f}}{s} + 1 \quad n^{[l]}_{W} = \frac{{n^{[l-1]}_{W} + 2p - f}}{s} + 1\\  \\

& \text{Each filter size}: (f^{[l]}, f^{[l]}, n^{[l-1]}_{c}) \\
& \text{Activations size}: a^{[l]} \to (n_{H}^{[l]}, n_{W}^{[l]}, n_{c}^{[l]}) \quad|\quad A^{[l]} \to (m, n_{H}^{[l]}, n_{W}^{[l]}, n_{c}^{[l]})  \\
& \text{Weights}: f^{[l]} \times f^{[l]} \times n_{c}^{[l-1]} \times n_{c}^{[l]}  \\
& Bias: n_{c}^{[l]} \to (1, 1, 1, n_{c}^{[l]})
\end{align}
$$


## Convolution summary
### Conv single layer summary
$$
\begin{align}
& n \times n \quad \text{image} \\
& f \times f \quad \text{filter}  \\
& p \quad \text{padding} \\
& s \quad \text{stride}  \\ \\
& \text{Output size}  \\
& \left\lfloor \begin{matrix}
\frac{{n + 2p - f }}{s} + 1
\end{matrix}
\right\rfloor \times \left\lfloor \begin{matrix}
\frac{{n + 2p - f }}{s} + 1
\end{matrix}
\right\rfloor
\end{align}
$$

## See more

