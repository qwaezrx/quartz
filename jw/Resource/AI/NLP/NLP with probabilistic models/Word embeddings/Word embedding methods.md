---
tags:
  - AI/NLP/Word-Embedding
---


## Classical methods
#### [[Word2Vec]]

#### [[CBOW]] (Continuous bag-of-words)
(Google, 2013)
- the model learns to predict the center word given some context words

#### [[SGNS]] (Conginuous skip-gram/Skip-gram with negative sampling)
- The model learns to predict the words surrounding a given input word.

#### [[GloVe]] (Global Vectors)
(Stanford, 2014)
- Factorizes the logarithm of the corpus's word co-occurrence matrix, similar to the count matrix you've used before

#### [[fastText]]
(Facebook, 2016)
- based on the skip-gram model and takes into account the structure of words by representing words as an n-gram of characters. It supports OOV words

## Deep learning, contextual embeddings
In these advanced models, words have different embeddings depending on their context. You can download pre-trained embeddings for the following models.
#### [[BERT]] 
(Google, 2018)

#### [[ELMo]]
(Allen Institute for AI, 2018)

#### [[GPT-2]]
(OpenAI, 2018)


## See more

- [OpenAI Embeddings](https://platform.openai.com/docs/guides/embeddings/what-are-embeddings)

