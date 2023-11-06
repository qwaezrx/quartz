[[Training]]
## mini-batch gradient descent

For example if $m$ = 5000000?
It will be better to create mini-batches of 1000 each

mini-batch t: $X^{\{t\}}, Y^{\{t\}}$ 

for t in 1...5000 {
	forward prop on $X^{\{t\}}$
	compute cost
	backprop for gradient descent
	update parameters
} -> 1 epoch (single pass through the training set)

## Batch vs. mini-batch gradient descent

Vectorization allows you to efficiently compute on $m$ examples.

- on batch [[Gradient descent]], there is only 1 gradient descent step
- on mini-batch gradient descent, there is multiple gradient descent steps for 1 epoch.

- mini-batch gradient descent is much faster than original batch gradient descent.

![[IMG_C5B837622E2A-1.jpeg]]


## Choosing mini-batch size
If mini-batch size == m : [[Batch gradient descent]] 
-> too long per iteration
If mini-batch size == 1: [[Stochastic gradient descent]]  
-> Lose speedup from vectorization

In between 1, m: mini-batch gradient descent
-> Fastest learning
	- [[Vectorization]]
	- Make progress without needing to wait training entire [[Training set]]

If small training set (m < 2000):
	Just use batch gradient descent

Typical mini-batch size:
	64, 128, 256, 512, (1024)

Make sure mini-batch fit in CPU/GPU memory