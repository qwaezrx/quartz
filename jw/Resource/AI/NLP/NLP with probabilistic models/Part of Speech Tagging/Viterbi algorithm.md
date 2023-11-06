
[[Markov Chain]]

## Viterbi algorithm - a graph algorithm
A matrix that can tell you the parts of speech tag of every word. This matrix will tell you the probability that every word belongs to a certain parts of speech tag.

![[Pasted image 20230902185857.png]]

![[Pasted image 20230902185903.png]]


## Viterbi initialization
Start by initializing two matrices of the same dimension.

- best_probs: Each cell contains the probability of going from one POS tag to a word in the corpus
- best_paths: A matrix that helps you trace through the best path in the corpus

__C__:

|         | $w_{1}$ | $w_{2}$ | $\dots$ | $w_{K}$ |
| ------- | ------- | ------- | ------- | ------- |
| $t_{1}$ |  $C_{1, 1}$   |         |         |         |
| $t_{2}$ |         |         |         |         |
| $\dots$ |         |         |         |         |
| $t_{N}$        | $C_{N, 1}$        |         |         |         |

The first column of the C represents probability of the translations from the start

$$
c_{i, 1} = \pi_{i} * b_{i, \text{cindex}(w_{1})} = a_{1, i} * b_{i, \text{cindex}(w_{1})}
$$

![[Pasted image 20230902212057.png]]

__D__:

|         | $w_{1}$ | $w_{2}$ | $\dots$ | $w_{K}$ |
| ------- | ------- | ------- | ------- | ------- |
| $t_{1}$ |  $d_{1, 1}$   |         |         |         |
| $t_{2}$ |         |         |         |         |
| $\dots$ |         |         |         |         |
| $t_{N}$        | $d_{N, 1}$        |         |         |         |


## Forward pass
$$
c_{i, j} = \max_{k} c_{k, j-1} * a_{k, i} * b_{i, \text{cindex}(w_{2})}
$$
$$
d_{i, j} = \text{arg}\max_{k} c_{k, j-1} * a_{k, i} * b_{i, \text{cindex}(w_{2})}
$$
![[Pasted image 20230902213047.png]]


## Backward pass

$$
\begin{align}
& s = \text{arg}\max_{i} c_{i, K}
\end{align}
$$
The probability at this index is the probability of the most likely sequence of hidden states generating the given sequence of words.

The matrix D stores all the labels of the hidden states you've traversed in the forward path.

![[Screenshot 2023-09-02 at 8.09.20 PM.png]]

![[Screenshot 2023-09-02 at 8.10.37 PM.png]]

![[Pasted image 20230902213932.png]]

```python
for i in range(0, 10, -1):
	print(i)
```