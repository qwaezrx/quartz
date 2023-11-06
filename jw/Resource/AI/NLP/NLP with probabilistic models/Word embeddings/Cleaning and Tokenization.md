---
tags:
  - AI/NLP/Word-Embedding
---

![[Pasted image 20230906034013.png]]

#### Cleaning & Tokenization Python example


```python
import nltk
import re

corpus = "Who 💔 'word embeddings' in 2020? I do!!!"

data = re.sub(r'[,!?;-]+', '.', corpus)
data = nltk.word_tokenize(data)

data = [
	ch.lower() for ch in data
	if ch.isalpha()
	or ch == '.'
	or emoji.get_emoji_regexp().search(ch)
]
```

