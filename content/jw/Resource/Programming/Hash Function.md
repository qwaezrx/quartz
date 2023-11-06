---
aliases:
  - hash function
---


When word vectors have just one dimension instead of 300 dimensions so each word is represented by a single number. You need to find a way to give each vector a _hash value_ which is a key that tells use which buckets in [[Hash table]] it's assigned to.

A function that assigns a [[Hash value]] is a _hash function_
$$
\text{Hash function(vector)} \to \text{Hash value}
$$

__Basic hash tabling (Python)__

```python

def basic_hash_table(value_1, n_buckets):
	def hash_function(value, n_buckets):
		return int(value) % n_buckets

	hash_table = {i:[] for i in range(n_buckets)}
	for value in value_1:
		hash_value = hash_function(value, n_buckets)
		hash_table[hash_value].append(value)
		
	return hash_table
```


__Hash Function - ETH__

<iframe width="560" height="315" src="https://www.youtube.com/embed/QJ010l-pBpE?si=l9ejGnCAOLc4gYmy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

