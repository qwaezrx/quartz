---
tags:
  - AI/RNN
---


```python

def forward_V_RNN(inputs, weights):
	"""
	Forward propagation for a single vanilla RNN cell
	"""
	x, h_t = inputs
	
	# weights
	wh, _, _, bh, _, _ = weights
	
	# new hidden state
	h_t = np.dot(wh, np.concatenate([h_t, x])) + bh
	h_t = sigmoid(h_t)
	
	return h_t, h_t
```

