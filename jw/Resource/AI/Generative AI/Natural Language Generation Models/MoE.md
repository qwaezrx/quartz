---
aliases:
  - Mixture of Experts
author: Google
date:
---


## Model of Experts
MoE has sparse connections between the models, dramatically reducing the parameters to be synchronized across instances.

- A number of experts -> Architecture of experts could diverge
- Trainable [[Gating network]] used to select a few experts per input.

## Models

```dataview
TABLE date, parameters, author
FROM #Model  AND #MoE 
SORT date DESC
```


## See More
- https://research.google/pubs/pub45929/