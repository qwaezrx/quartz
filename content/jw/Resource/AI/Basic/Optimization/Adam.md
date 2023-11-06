
- Adam is one of the most effective [[Optimization algorithms for training NN]]
- Basically taking [[Gradient descent with momentum]] and [[RMSProp]] and putting them together


```pseudo
\begin{algorithm}
\caption{Adam optimization algorithm}
\begin{algorithmic}
\State $V_{dW} = 0, S_{dW} = 0$
\State $V_{db} = 0, S_{db} = 0$
\State $B$: number of mini-batches
\State $\alpha$: needs to be tuned
\State $\beta_1: 0.9$ \comment{<-$dw$ momentum like term}
\State $\beta_2: 0.99$ \comment{<-$dw^2$ RMSprop like term}
\State $\epsilon: 10^{-8}$ \comment{Usually use default value}
\For{$t = 1$ \To B}
	\State Compute $dW, db$ using current mini-batch
	\State $V_{dW} = \beta_1 V_{dW} + (1-\beta_1) dW$
	\State $V_{db} = \beta_1 V_{db} + (1-\beta_1) db$ 
	\Comment{V -> "Momentum" like}
	\State $S_{dW} = \beta_2 S_{dW} + (1-\beta_2) dW^2$
	\State $S_{db} = \beta_2 S_{db} + (1-\beta_2) db^2$
	\Comment{S -> "RMSprop like"}
	\State $V_{dW}^{corrected} = V_{dW}/(1-(\beta_1)^t)$
	\State $V_{db}^{corrected} = V_{db}/(1-(\beta_1)^t)$
	\State $S_{dW}^{corrected} = S_{dW}/(1-(\beta_2)^t)$
	\State $S_{db}^{corrected} = S_{db}/(1-(\beta_2)^t)$
	\State $W:= W - \alpha \frac{V_{dW}^{corrected}}{\sqrt{S_{dW}^{corrected}} + \epsilon}$
	\State $b:= b - \alpha \frac{V_{db}^{corrected}}{\sqrt{S_{db}^{corrected}} + \epsilon}$
\EndFor
\end{algorithmic} 
\end{algorithm}
```


