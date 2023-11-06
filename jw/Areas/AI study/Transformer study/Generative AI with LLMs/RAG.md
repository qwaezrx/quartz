---
aliases:
  - Retrieval Augmented Generation
---

## Retrieval Augmented Generation

![[Screenshot 2023-09-05 at 8.13.18 PM.png]]

## Retriever
- __Query encoder__

- __External information sources__
Usually it uses [[Vector database]], but can use other types of db too (SQL, CSV files, etc.).

These two components are trained together to find documents within the external data that are most relevant to the input query.

The retriever returns the best single or group of documents form the data source, and combines the new information with the original user query.

This expanded prompt is then passed to the language model, which generates a completion that makes use of the data.

#### External information sources
- Documents
- Wikis
- Expert systems
- Web pages
- Databases
- Vector store

## Data preparation for vector store for RAG
Two considerations for using external data in RAG:
1. Data must fit inside [[Context window]]
2. Data must be in format that allows its relevance to be assessed at inference time: [[Embedding]] vectors


