---
aliases:
  - execution client
  - execution clients
tags:
  - Blockchain/Ethereum
---


The _execution client_ is: 
- responsible for:
	- [[Transaction]] handling
	- transaction gossip
	- state management
	- supporting [[EVM]]
- __Not__ responsible for:
	- block building
	- block gossiping
	- handling consensus logic
	Which are in the remit of the [[Consensus client]].

The execution client creates execution payloads - the list of transactions, updated state trie, and other execution-related data. 
[[Consensus client]]s include the execution payload in every block.The execution client is also responsible for re-executing transactions in new blocks to ensure they are valid. Executing transactions is done on the execution client's embedded computer, known as the [[EVM]].

The execution client offers a user interface to Ethereum through [[RPC|RPC methods]] that enable users to query the Ethereum blockchain, submit transactions and deploy smart contracts. It's common for RPC calls to be handled by a library like [Web3js](https://docs.web3js.org/), [Web3py](https://web3py.readthedocs.io/en/v5/), or by a user-interface such as a browser wallet.

In summary, the execution client is:
- a user gateway to Ethereum
- home to the [[EVM]], Ethereum's state and transaction pool.


## See More
---
- [[Geth]]