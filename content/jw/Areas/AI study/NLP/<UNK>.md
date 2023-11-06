---
tags:
  - AI/NLP/Word-Embedding
---


## Out of vocabulary words
- Closed vs. Open vocabularies
- Unknown word = Out of vocabulary word (OOV)
- special tag \<UNK> in corpus and in input


## Using \<UNK> in corpus
- Create vocabulary V
- Replace any word in corpus and not in V by \<UNK>
- Count the probabilities with \<UNK> as with any other word


## How to create vocabulary V
- Criteria:
	- Min word frequency f
	- Max |V|, include words by frequency
- Use \<UNK> sparingly
- [[Perplexity]] - only compare LMs with the same V


