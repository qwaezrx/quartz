
단순히 모든 기울기를 더하는 것이 아니라 최신 기울기 정보를 더 크게 반영.
- with [[EMA]]

## Root mean squared prop
- Can speed up [[Gradient descent]]

```pseudo
\begin{algorithm}
\caption{RMSprop}
\begin{algorithmic} 
\For{i = 1 \To t}
	\State Compute $dW, db$ on current mini-batch
	\State $S_{dW} = \beta S_{dW} + (1-\beta) dW^{2}$ \Comment{<- small}
	\State $S_{db} = \beta S_{db} + (1-\beta) db^{2}$ \Comment{<- large}
	\State $W:= W - \alpha \frac{dW}{\sqrt{S_{dW}} + \epsilon}$
	\State $b:= b - \alpha \frac{db}{\sqrt{S_{db}} + \epsilon}$
\EndFor
\end{algorithmic}
\end{algorithm}
```

- $\epsilon$ : 
	- 기울기가 무한히 커지는 것을 방지
	- 작을수록 최신의 정보를 더 크게 반영