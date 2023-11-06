---
tags:
  - AI/Loss_Function
---

$$
L_{\text{Contrastive}} = (1-Y) \frac{1}{2}(D_{W})^{2} + (Y) \frac{1}{2} (max(0, m-D_{W}))^{2}
$$

_Contrastive Loss Function_ 은 두 가지 input pair를 사용하며, 두 데이터의 라벨이 같을 경우 gamma는 0 아닐 경우, 1이 된다.
Negative sampling 에 대해서 margin 값보다 더 멀어지지 않게 하기 위해서 max 제약을 걸어놓는다.

