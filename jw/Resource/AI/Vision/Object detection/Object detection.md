---
tags:
  - AI/CV/Object-Detection
---

![[IMG_D1DFBB963A6C-1.jpeg]]

## Defining the target label y

1 - pedestrian
2 - car 
3 - motorcycle
4 - background

Need to output $b_{x}, b_{y}, b_{h}, b_{w}$, class label (1-4)

$$
y = \begin{pmatrix}
p_{c} \\
b_{x} \\
b_{y}  \\
b_{h} \\
b_{w} \\
c_{1} \\
c_{2} \\
c_{3} \\
\vdots
\end{pmatrix}
$$
$p_{c}$: is there an object?


## Landmark detection
In more general cases, you can have a NN just output x, y coordinates (landmarks) of important points and image.

$$
y = \begin{pmatrix}
\text{face?} \\
l_{1x} \\
l_{1y} \\
l_{2x} \\
l_{2y} \\
\vdots
\end{pmatrix}
$$

## Sliding windows detection
Run ConNet for every position of the window.
Should use large stride
change the window size and repeat

Requires very high COCO.






