---
tags:
  - AI
  - CS/Programming/Python/NumPy
---


# 1 - Packages
- [[NumPy]] is the main package for scientific computing with [[Python]].

```python
import numpy as np
import h5py
import matplotlib.pyplot as plt

%matplotlib inline
plt.rcParams[“figure.figsize“] = (5.0, 4.0) # set default size of plots
plt.rcParams[”image.interpolation”] = “nearest”
plt.rcParams[“image.cmap”] = “gray”

%load_ext autoreload
%autoreload 2

np.random.seed(1)
```

# 2 - Outline
![[Pasted image 20230826111342.png]]

To build a [[DNN]], first yo need to implement several “helper functions.”

Each small helper function will have detailed instructions to walk you through the necessary steps. Here’s an outline of the steps in this assignment:
- Initialize the parameters for a two-layer network and for an $L$- layer neural network
- Implement the __forward propagation__ module (shown in purple in the figure above)
	- Complete the LINEAR part of a layer’s forward propagation step (resulting in $Z^{[l]}$).
	- Create the activation functions
	- Combine the previous two steps into a new LINEA -> ACTIVATION forward function.
	- Stack the LINEAR->RELU forward function L-1 times (for layers 1 to L-1) and add a LINEAR->SIGMOID at the end (for the final layer L). This gives you a new L_model_forward function.
- Compute the loss
- Implement the __backward propagation__ module (denote in red in the figure below)
	- Complete the LINEAR part of a layer’s backward propagation step
	- The gradient of the ACTIVATION function is provided for you(relu_backward/sigmoid_backward)
	- Combine the previous two steps into a new LINEAR->ACTIVATION backward function
	- Stack LINEAR->RELU backward L-1 times and add LINEAR->SIGMOID backward in a new L_model_backward function
- Finally, update the parameters

>[!note]
>For every forward function, there is a corresponding backward function. This is why at every step of your forward module you will be storing some values in a cache. These cached values are useful for computing gradients.
>
>In the backpropagation module, you can then use the cache to calculate the gradients. 


# 3 - Initialization
## 3.1 - L-layer Neural Network

```python
from typing import Dict, List

def initialize_parameters_deep(layer_dims: List[int]) -> Dict[str, np.ndarray]:
	parameters = {}
	L = len(layer_dims) # number of layers in the network

	for l in range(1, L):
		parameters[“W” + str(l)] = np.random.randn(layer_dims[l], layer_dims[l-1]) * 0.01
		parameters[“b” + str(l)] = np.zeros((layer_dims[l], 1))
	return parameters
```


# 4 - Forward propagation module

## 4.1 - Linear forward
```python
def linear_forward(A, W, b):
	Z = np.dot(W, A) + b
	cache = (A, W, Z)
	return Z, cache
```

## 4.2 - Linear-activation forward
- [[Sigmoid]]
- [[ReLU]]

```python
def linear_activation_forward(A_prev, W, b, activation: str):
	return A, cache
```

## 4.3 - L-layer model
```python
def L_model_forward(X, parameters):
	caches = []
	A = X
	L = len(parameters) // 2
	for l in range(1, L):
		A_prev = A
		A, cache = linear_activation_forward(A_prev, parameters["W" + str(l)], parameters["b" + str(l)], "relu")
        caches.append(cache)

	AL, cache = linear_activation_forward(A, parameters["W" + str(L)], parameters["b" + str(L)], "sigmoid")
	caches.append(cache)
	
	return AL, caches
```

# 5 - Cost function
Compute the cross-entropy cost $J$, using the following formula:

$$
\begin{align}
- \frac{1}{m}\sum^{m}_{i=1}(y^{(i)}\log a^{[L](i)} + (1-y^{(i)})\log(1-a^{[L](i)}))
\end{align}
$$
```python
from numbers import Number

def compute_cost(AL, Y) -> Number:
	m = Y.shape[1]
	
	cost = - 1/m * ( np.dot(Y, AL.T) + np.dot(-(Y-1), np.log(-(AL-1)).T )
	cost = np.squeeze(cost) # e.g.  this turns [[17]] into 17
	return cost
```

# 6 - Backward propagation module

__Reminder__:
![[Pasted image 20230826124211.png]]

## 6.1 - Linear backward

![[Pasted image 20230826124835.png]]

$$
\begin{align}
& dW^{[l]} = \frac{\partial \mathcal{J}}{\partial W^{[l]}} = \frac{1}{m} dZ^{[l]]}A^{[l-1]T}  \\
& db^{[l]} = \frac{\partial \mathcal{J}}{\partial b} = \frac{1}{m} \sum^{m}_{i=1}dZ^{[l](i)}  \\
& dA^{[l-1]} = \frac{\partial\mathcal{L}}{\partial A^{[l-1]}}= W^{[l]T}dZ^{[l]}
\end{align} 
$$
```python
def linear_backward(dZ, cache):
	A_prev, W, b = cache
	m = A_prev.shape[1]

	dW = 1/m * np.dot(dZ, A_prev.T)
	db = 1/m * np.sum(dZ, axis=1, keepdims=True)
	dA_prev = np.dot(W.T, dZ)
	return dA_prev, dW, db
```

## 6.2 - Linear-activation backward

If $g(.)$ is the activation function, `sigmoid_backward` and `relu_backward` compute:
$$
dZ^{[l]} = dA^{[l]} * g’(Z^{[l]})
$$

```python

def linear_activation_backward(dA, cache, activation: str):
	linear_cache, activation_cache = cache
	…
	return dA_prev, dW, db
```
## 6.3 - L-model backward

```python
def L_model_backward(AL, Y, caches):
	grads = {}
	L = len(caches)
	m = AL.shape[1]
	Y = Y.reshape(AL.shape) # after this line, Y is the same shape as AL.

	dAL = - (np.divide(Y, AL) - np.divide(1 - Y, 1 - AL)) # derivative of cost with respect to AL
	current_cache = caches[L-1]
	dA_prev_temp, dW_temp, db_temp = linear_activation_backward(dAL, current_cache, “sigmoid”)
	…
	for l in reversed(range(L-1)):
		…

	return grads
```

## 6.4 - Update parameters

```python

def update_parameters(params, grads, learning_rate):
	parameters = params.copy()
	L = len(parameters) // 2

	for l in range(L):
		parameters["W" + str(l+1)] =parameters["W" + str(l+1)] - learning_rate * grads["dW" + str(l + 1)]
        parameters["b" + str(l+1)] =parameters["b" + str(l+1)] - learning_rate * grads["db" + str(l + 1)]
        
	return parameters
```

