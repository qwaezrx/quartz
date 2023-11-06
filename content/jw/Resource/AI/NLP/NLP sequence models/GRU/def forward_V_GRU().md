

```python

def forward_V_GRU(inputs, weights):
	x, h_t = inputs
	wu, wr, wc, bu, br, bc = weights
	
	# Update gate
	G_u = np.dot(wu, np.concatenate([h_t, x])) + bu
	G_u = sigmoid(G_u)
	
	# Relevance gate
	G_r = np.dot(wr, np.concatenate([h_t, x])) + br
	G_r = sigmoid(G_r)
	
	# Candidate hidden gate
	G_c = np.dot(wc, np.concatenate([G_r * h_t, x])) + bc
	G_c = np.tanh(c)
	
	# New hidden state h_t
	h_t = G_u * c + (1 - G_u) * h_t
	
	return h_t, h_t

```

