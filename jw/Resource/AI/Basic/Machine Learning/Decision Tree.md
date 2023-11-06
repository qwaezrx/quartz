---
tags:
  - AI/ML
---


The basic intuition behind a decision tree is to map out all possible decision paths in the form of a tree.

## Decision tree learning algorithm
1. Choose an attribute from your dataset
2. Calculate the significance of attribute in splitting of data
3. Split data based on the value of the best attribute
4. Go to step 1


#### Which attribute is the best?
- More __Predictiveness__
- Less __Impurity__
- Lower __Entropy__
![[Screenshot 2023-09-09 at 12.00.13 AM.png]]

#### Entropy
- Measure of randomness or uncertainty

$$
\text{Entropy} = - p(A) \log_{2}(p(A)) - p(B)\log_{2}(p(B))
$$

$$
\text{Information gain} = (\text{Entropy before split}) - (\text{weighted entropy after split})
$$


## See more
- [[Decision tree in sklearn]]

