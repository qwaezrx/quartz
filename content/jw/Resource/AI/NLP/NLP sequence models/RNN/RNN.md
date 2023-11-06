---
tags:
  - AI/RNN
---


### Why not standard network
Problems:
- Inputs, outputs can be different lengths in different examples ([[Sequence data]])
- Doesn't share features learned across different positions of text

The RNN scans the data from left to right

![[Pasted image 20230906143310.png]]


![[RNN.jpeg]]

![[Pasted image 20230906143433.png]]


## [[RNN unit.canvas|RNN unit]]

![[Pasted image 20230829191418.png]]

![[Pasted image 20230906144114.png]]


## Parameters

$W_{ax}$ 
$W_{ya}$
$W_{aa}$

## Weakness of RNN
One weakness of RNN is that it only uses the information that is __earlier__ in the sequence to make a prediction

[[BRNN]]: Bidirectional RNN

## RNN; Forward propagation

![[RNN_cell_forward_sequential.png]]

$$
\begin{align}
& a^{<0>} = \vec{0}  \\
& a^{<1>} = g_{1}(W_{aa}a^{<0>} + W_{ax}x^{<1>} + b_{a}) \\
& \hat{y}^{<1>} = g_{2}(W_{ya}a^{<1>} + b_{y})
\end{align}
$$

- $g_{1}$: $tanh$ is common choice for activation function($g_{1}$), or $ReLU$
- $g_{2}$: sigmoid is common choice

### Simplified RNN notation
$$
\begin{align}
& a^{<t>} = g_{1}(W_{aa}a^{<t-1>} + W_{ax}x^{<t>} + b_{a}) \\
& \hat{y}^{<t>} = g_{2}(W_{ya}a^{<t>} + b_{y}) \\ \\
& W_{a} = \begin{bmatrix}
W_{aa} | W_{ax}
\end{bmatrix} \\
& a^{<t>} = g_{1}(W_{a}[a^{<t-1>}, x^{<t>}] + b_{a}) \\
& \hat{y}^{<t>} = g_{2}(W_{ya}a^{<t>} + b_{y})
\end{align}
$$


## RNN; Backpropagatioin

$$
\begin{align}
& \mathcal{L}^{<t>}(\hat{y}^{<t>}, y^{<t>}) = -y^{<t>}\log \hat{y}^{<t>} - (1 - y^{<t>})\log (1-\hat{y}^{<t>})  \\
& \mathcal{L}(\hat{y}, y) = \sum^{T}_{t=1}\mathcal{L}^{<t>}(\hat{y}^{<t>}, y^{<t>})
\end{align}
$$


## Different types of RNNs

- Many-to-many
- Many-to-one
	- Sentiment analysis

![[IMG_66CE7D53FD2E-1.jpeg]]

- One-to-many
	- Text generation
	- Music generation
		- $x \to y^{<1>}y^{<2>}\dots y^{<T_{y}>}$

	
![[IMG_E5A7B4BA1427-1.jpeg]]


![[IMG_24109C3A3061-1.jpeg]]

- [[Deep RNN]]
- [[Bi-directional RNNs]]

## Vanishing gradients with RNNs

![[Pasted image 20230906172411.png]]

__Solutions to vanishing gradient problems__:
- Identity  RNN with ReLU activation
- [[Gradient clipping]]
- Skip connections

![[Pasted image 20230906172545.png]]

__Models to solve vanishing gradients problems in RNNs:__
- [[GRU]]
- [[LSTM]]


## RNN; Cost function
__RNN [[Cross Entropy Loss]]__
$$
J = -\frac{1}{T}\sum^{T}_{t=1}\sum^{K}_{j=1} y^{<t>}_{j} \log \hat{y}^{<t>}_{j}
$$
- For RNNs the loss function is just an average through time



## Backpropagation in RNN

![[Pasted image 20230829232411.png]]




## Important features of RNN
- The RNN is essentially the repeated use of a single cell.

- A basic RNN reads inputs one at a time, and remembers information through the hidden layer activations (hidden states) that are passed from one time step to the next.
	- The time step dimension determines how many times to re-use the RNN cell

- Each cell takes two inputs at each time step:
	- The hidden state from the previous cell
	- The current time step’s input data

- Each cell has two outputs at each time step:
	- A hidden state
	- A prediction


- “Exploding” gradients updates can be a problem 
	- $\therefore$ Clip gradients before updating the parameters

- Sampling is a technique you can use to pick the index of the next character according to a probability distribution.

- Can only train one token at a time
	- No Training parallelism

