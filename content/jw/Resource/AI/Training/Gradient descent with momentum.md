---
tags:
  - AI/Training
---


```pseudo
    \begin{algorithm}
    \caption{Gradient descent with momentum example}
    \begin{algorithmic}
      \PROCEDURE{Momentum}{$t, \alpha,\beta$}
        \For{$i = 1$ \To $t$}
	        \State Compute dW, db on current mini-batch
	        \State $V_{dW} = \beta V_{dW} + (1-\beta)dW$ \Comment{$V \approx velocity, dW \approx acceleration$}
			\State $V_{db} = \beta V_{db} + (1-\beta)db$

			\State $W = W - \alpha V_{dW}$
			\State $b = b - \alpha V_{db}$
        \EndFor
      \ENDPROCEDURE
      \end{algorithmic}
    \end{algorithm}
```


