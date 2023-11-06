---
tags:
  - CS/Programming/Python/Tensorflow
---


```python

def scan(fn, elems, initializer=None, ...):
	cur_value = initializer
	ys = []

	for x in elems:
		y, cur_value = fn(x, cur_value)
		ys.append(y)

	return ys, cur_value
```

The scan function is designed to take a function `fn` and apply it to all of the elements from the beginning to the end


![[Pasted image 20230906153437.png]]


- Frameworks require abstractions
- `tf.scan()` mimics [[RNN]]s

