---
tags:
  - AI/CV/Face-Recognition
---

[[Siamese network; CNN]]

## Face verification vs. Face recognition
#### Verification
- Input image, name/ID
- Output whether the input image is that of the claimed person

#### Recognition
- Has a database of K persons
- Get an input image
- Output ID if the image is any of the K persons (or "not recognized")


## Learning a "similarity" function
d(img1, img2) = degree of difference between images

__Verification__
$\text{if } d(img1, img2) \leq \tau$   => "same"
                           $> \tau$    => "different"

