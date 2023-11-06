---
tags:
  - Blockchain/Ethereum
---

[[Ethereum]] is a distributed network of computers (known as _nodes_) running software that can verify blocks and transaction data. The software must be run on your computer to turn it into an Ethereum node.

An _Ethereum node_ is composed of two pieces of software, known as clients:
1. [[Execution client]]
2. [[Consensus client]]

When [[Ethereum]] was using [[PoW]], an execution client was enough to run a full Ethereum node. However, since implementing [[PoS]], the execution client needs to be used alongside another piece of software called a [[Consensus client]].


__Relationship between the two Ethereum clients:__  
![](https://ethereum.org/static/bd74c6965c42fd5c981790c45437f83f/280a1/node-architecture-text-background.png)
The two clients connect to their own respective P2P networks. Separate P2P networks are needed as the execution clients gossip transactions over their P2P network, enabling them to manage their local transaction pool, whilst the consensus clients gossip blocks over their P2P network, enabling consensus and chain growth.



## Resources
- https://ethereum.org/en/developers/docs/nodes-and-clients/node-architecture/#node-comparison