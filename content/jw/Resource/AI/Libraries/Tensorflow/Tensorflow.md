---
tags:
  - Open_Source
  - CS/Programming/Python/Tensorflow
  - AI
---


```python
import numpy as np
import tensorflow as tf
```

```python
w = tf.Variable(0, dtype=tf.float32)
optimizer = tf.keras.optimizers.Adam(0.1)

def train_step():
	with tf.GradientTape() as tape:
		cost = w ** 2 - 10 * w + 25
	trainable_variables = [w]
	grads = tape.gradient(cost, trainable_variables)
	optimizer.apply_gradients(zip(grads, trainable_variables))

print(w)
```

```python
train_step()
print(w)
```

```python
w = tf.Variable(0, dtype=tf.float32)
x = np.array([1.0, -10.0, 25.0], dtype=np.float32)
optimizer = tf.keras.optimizers.Adam(0.1)

def cost_fn():
	return x[0] * w ** 2 + x[1] * w + x[2]

print(w)
optimziers.minimize(cost_fn, [w])
print(w)
```

