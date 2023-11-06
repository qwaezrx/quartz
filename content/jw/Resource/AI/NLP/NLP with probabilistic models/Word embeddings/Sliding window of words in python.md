---
tags:
  - AI/NLP/Word-Embedding
---

This `get_windows` function is for [[CBOW]]

```python
def get_windows(words, C):
	i = C
	while i < len(words) - C:
		center_word = words[i]
		context_words = words[(i-C):i] + words[(i+1):(i+C+1)]
		yield context_words, center_word
		i += 1
```