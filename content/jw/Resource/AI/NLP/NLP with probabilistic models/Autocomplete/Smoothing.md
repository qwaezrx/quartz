

Smoothing prevents the probability being zero on [[N-Grams]]


#### __Add-one smoothing (Laplacian smoothing)__
$$
\begin{align}
& P(w_{n} \mid w_{n-1}) = \frac{{C(w_{n-1}, w_{n}) + 1}}{\sum_{w \in V}(C(w_{n-1}, w) + 1)} = \frac{{C(w_{n-1}, w_{n}) + 1}}{C(w_{n-1}) + V}
\end{align}
$$

#### __Add-k smoothing__
- Use when you have large corpus

$$
\begin{align}
& P(w_{n} \mid w_{n-1}) = \frac{{C(w_{n-1}, w_{n}) + k}}{\sum_{w \in V}(C(w_{n-1}, w) + k)} = \frac{{C(w_{n-1}, w_{n}) + k}}{C(w_{n-1}) + V * k}
\end{align}
$$

#### Advanced methods:
- Kneser-Ney smoothing
- Good-Turing smoothing



