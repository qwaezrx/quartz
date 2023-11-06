---
tags:
  - CS/Programming/Python
---


```python
from collections import defaultdict

freq = defaultdict(int)

words = ["a", "b", "a", "c"]

for word in words:
	freq[word] += 1

print(freq)
```

