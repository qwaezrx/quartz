---
tags:
  - AI/CV/Object-Detection
---

Each output prediction
$$
\begin{pmatrix}
p_{c} \\
b_{x} \\
b_{y} \\
b_{h} \\
b_{w} \\
\end{pmatrix}
$$
discard all boxes $p_{c} < 0.6$
While there are any remaining boxes:
- Pick the box with the largest $p_{c}$ output that as a prediction
- Discard any remaining box with [[IoU]] $\geq$ 0.5 with the box output in the previous step


