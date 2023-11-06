
Layer class which is similar to the one used in [[Trax]] , [[PyTorch]], [[Tensorflow]]

```python

class Layer(object):
	def __init__(self):
		self.weights = None

	def forward(self, x):
		raise NotImplementedError

	def init_weights_and_state(self, input_signature, random_key):
		pass

	def init(self, input_signature, random_key):
		self.init_weights_and_state(input_signature, random_key)
		return self.weights

	def __call__(self, x):
		return self.forward(x)

```