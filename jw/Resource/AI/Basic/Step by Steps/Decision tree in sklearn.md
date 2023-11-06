---
tags:
  - CS/Programming/Python/Scikit-Learn
  - AI/ML
---

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)
```

```python
from sklearn.tree import DecisionTreeClassifier

drugTree = DecisionTreeClassifier(criterion="entropy", max_depth=4)
drugTree
```

```python
drugTree.fit(X_train, y_train)
```

```python
pred = drugTree.predict(X_test)
```

```python
from sklearn import metrics

print("DecisionTree's Accuracy: ", metrics.accuracy_score(y_test, pred))
```

