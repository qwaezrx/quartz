---
tags:
  - AI/ML
---

## Support Vector Machine

>SVM is a [[Supervised ML]] algorithm that classifies cases by finding a separator

1. Mapping data to a __high-dimensional__ feature space
2. Finding a __separator__

- SVM algorithm outputs an optimal hyperplane that categorizes new examples
- Used for classification

![[Screenshot 2023-09-09 at 12.14.32 AM.png]]

#### Kernelling:
- Linear
- Polynomial
- RBF
- Sigmoid


![[Screenshot 2023-09-09 at 12.25.15 AM.png]]


## Pros and cons of SVM
- + Accurate in high-dimensional spaces
- + Memory efficient

- - Prone for [[Overfitting]]
- - No probability estimation
- - Works well only on small dataset


## SVM applications
- [[Image recognition]]
- Text category assignment
- Detecting spam
- Sentiment analysis
- Gene Expression Classification
- Regression, outlier detection and clustering


## SVM; sklean


```python
from sklearn import svm

clf = svm.SVC(kernel='rbf')
clf.fit(X_train, y_train)
```

