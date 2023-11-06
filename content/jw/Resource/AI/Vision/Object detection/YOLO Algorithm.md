---
tags:
  - AI/CV/Object-Detection
---

## You only look once

$$
y.\text{shape} = (\text{grid}_{x}, \text{grid}_{y}, \text{anchors}, \text{classes})
$$

![[Screenshot 2023-09-01 at 7.07.05 PM.png]]

(100, 100, 3) -> ConvNet -> (3, 3, 16)

![[Screenshot 2023-09-01 at 7.11.06 PM.png]]

## Outputting the non-max supressed outputs
[[Non-max suppression algorithm]]

- For each grid cell, get 2 (anchors) predicted bounding boxes
- Get rid of low probability predictions
- For each class (pedestrian, car, motorcycle) use non-max suppression to generate final predictions


