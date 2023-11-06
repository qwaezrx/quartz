---
aliases:
  - markov chains
---


>A [[Stochastic model]] that describes a sequence of possible events

The word stochastic just means random or randomness.


![[Markov_chain_example.png]]
- E, A are states
- Arrows are transition probabilities

- Markov chains are important in [[Speech recognition]]. 


## Transition matrix

![[Transition_matrix.jpeg]]


$$
\begin{align}
& Q = \{ q_{1}, \dots , q_{N} \} & A = \begin{pmatrix}
a_{1, 1}  & \dots  & a_{1, N} \\
\vdots  & \ddots & \vdots \\
a_{N+1, 1} & \dots & a_{N+1, N} 
\end{pmatrix}  \\
&Q:= \text{States} \\
& A := \text{Transition matrix with initial state}
\end{align}
$$

## Transition probabilities
1. Count occurrences of tag pairs
$$
C(t_{i-1}, t_{i})
$$
2. Calculate probabilities using the counts
$$
P(t_{i}|t_{i-1}) = \frac{C(t_{i-1}, t_{i})}{\sum^{N}_{j=1}C(t_{i-1}, t_{j})}
$$

## Corpus
#### Preparation of the corpus
1. Split into sentences
2. lowercase

## Populating the Transition matrix
$$
\begin{align}
P(t_{i}|t_{i-1}) = \frac{{C(t_{i-1}, t_{i}) + \epsilon}}{\sum_{j=1}^{N}C(t_{i-1}, t_{j}) + N * \epsilon}
\end{align}
$$

## Emission probabilities

![[IMG_3A3EFE598F6C-1.jpeg]]

$$
P(w_{i}|t_{i}) = \frac{{C(t_{i}, w_{i}) + \epsilon}}{\sum^{V}_{j=1}C(t_{i}, w_{j}) + N * \epsilon} = \frac{{C(t_{i}, w_{i}) + \epsilon}}{C(t_{i}) + N * \epsilon}
$$


# Hidden Markov model


![[IMG_98178F10D1B1-1.jpeg]]

$$
\begin{align}
& \sum^{V}_{j=1}b_{ij} = 1
\end{align}
$$

$$
\begin{align}
& Q = \{ q_{1}, \dots , q_{N} \}  \\ \\

& A = \begin{pmatrix}
a_{1, 1}  & \dots  & a_{1, N} \\
\vdots  & \ddots & \vdots \\
a_{N+1, 1} & \dots & a_{N+1, N} 
\end{pmatrix} \\ \\
& B = \begin{pmatrix}
b_{1, 1}  & \dots  & b_{1, V} \\
\vdots  & \ddots & \vdots \\
b_{N, 1} & \dots & b_{N, V} 
\end{pmatrix}  \\ \\

&Q:= \text{States} \\
& A := \text{Transition matrix with initial state} \\
& B := \text{Emission matrix}
\end{align}
$$

