---
tags:
  - AI/Training
---

[[Hyperparameters]]


>[!important]
>Try random values for hyperparameters: Don't use grid

# Using an appropriate scale to pick hyperparameters

Pick samples in log scale:
```python
import numpy as np

r = -4 * np.random.rand()
learning_rate = 10 ** r
```

## Hyperparameters for [[Exponentially weighted averages]]

- $\beta$ = 0.9 ... 0.999
- $1 - \beta$ = 0.1 ... 0.001

```python
r = -2 * np.random.rand()
beta = learning_rate = 1 - 10 ** (r - 1)
```

# Hyperparameters tuning approaches

![[Screenshot 2023-08-27 at 1.14.57 AM.png]]

- Panda approach: Babysitting one model
- Cavia approach: Training many models in parallel



### 4.1.3 - Pruning