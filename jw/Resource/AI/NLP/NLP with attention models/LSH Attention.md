
Select nearest neighbors (K, Q) and return corresponding V

- [[KNN]]

## Locality Sensitive Hashing Attention

Compute the nearest neighbor to q among vectors $\{ k_{1}, \dots, k_{n} \}$
- Attention computes $d(q, k_{i}) \quad i \in \{ 1 \dots n \}$ which can be slow
- Faster approximate uses [[LSH]]

- Locality sensitive: if $q$ is close to $k_i$:
	$hash(q) == hash(k_{i})$

- Achieve by randomly cutting space
	$hash(x) = sign(xR) \quad R: [d, \text{n\_hash\_bins}]$


![[Pasted image 20230908204020.png]]


