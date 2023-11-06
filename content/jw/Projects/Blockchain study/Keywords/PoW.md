---
aliases:
  - Proof-of-Work
  - proof-of-work
tags:
  - Blockchain
---


_Nakamoto consensus_, which utilizes _proof-of-work_, is the mechanism that once allowed the decentralized Ethereum network to come to consensus (i.e. all nodes agree) on things like account balances and the order of transactions. This prevented users from __double sending__ their coins and ensured that the Ethereum chain was tremendously difficult to attack or manipulate.


## Example Python Code
---
```python
import hashlib
import time

def proof_of_work(prev_proof):
	new_proof = 1
	check_proof = False

	while check_proof is False:
		hash_operation = hashlib.sha256(str(new_proof**2 - prev_proof**2).encode()).hexdigest()
		if hash_operation[:4] == '0000': # The problem difficulty is defined here.
			check_proof = True
		else:
			new_proof += 1

	return new_proof

if __name__ == "__main__":
	start_time = time.time()
	print("New PoW: ", proof_of_work(20))
	print("--- {} seconds ---".format(time.time() - start_time))
			
```


## See More
---
- https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/