---
tags:
  - AI
---


$$
L_{\text{Angular}} = max(0, \begin{Vmatrix}
G_{W}(X) - G_{W}(X^{P})
\end{Vmatrix}_{2} - 4\tan ^{2} \alpha \begin{Vmatrix}
G_{W}(X^{n}) - G_{W}(X^{c})
\end{Vmatrix}_{2} )
$$


- [[Triplet Loss]] function의 경우, anchor와 positive, anchor와 negative 간의 짝을 보지만, 3가지 위치를 동시에 보지 못하는 문제가 발생함에 따라, 한 쪽을 optimize하면 다른 한 쪽의 성능이 저하될 우려가 있는데, 세 가지 데이터 간 거리를, 삼각형의 각의 관점에서 보면서, negative data point 가 가지고 있는 내각에 조건을 주는 방식 사용
- anchor/positive/negative 세 데이터 포인트가 요구하는 거리 조건을 동시에 충족시키면서 모델을 optimize할 수 있게 함.

