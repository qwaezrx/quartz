---
tags:
  - Blockchain
aliases:
  - blockchain
  - blockchains
---

## Introduction
---
_blockchain_: public database that is updated and shared across many computers in a network.
- [[Block]]: data and state being stored in consecutive groups known as _blocks_. 
- __Chain__: refers to the fact that each block cryptographically references its parent. In other words, blocks get chained together. 

The data in a block cannot change without changing all subsequent blocks, which would require the consensus of the entire network.

Every computer in the network must agree upon each block and the chain as a whole. These computers are known as "[[Node|nodes]]". Nodes ensure everyone interacting with the blockchain has the same data. To accomplish this distributed agreement, blockchains need [[Consensus Mechanism|consensus mechanisms]].



A blockchain is about enabling peer-to-peer transaction in a _decentralized network_. Establishing trust among unknown peers. Recording the transaction in an immutable distributed ledger. 

#### Centralized vs. Decentralized Transaction
- __Centralized__:
	1. Credit card agency
	2. Customer bank
	3. Credit card's bank
	4. Exchange
	5. Merchant's bank
	6. Merchant
- __Decentralized__:
	- Peer to peer directly

How do we establish trust among the peers in such a decentralized system?
1. Record the transaction in a distributed ledger of blocks
2. Create a tamper-proof record(chain) of blocks
3. Implement a consensus protocol for agreement on the block to be added to the chain

Key points:
- Validation
- Verification
- Consensus
- Immutable Recording

Validation, verification methods devised by the blockchain and implemented by the peers provide the collector trust needed in a decentralized system.


## Summary
---
Blockchain technology supports methods for a decentralized peer-to-peer system, a collective trust model, and a distributed immutable ledger of records of transactions. 


## Additional Information
---
[[Blockchain]] networks such as Bitcoin and Ethereum are immutable ledgers secured by a _decentralized network of computers_, known as "__block producers__", including miners in PoW blockchains and validators in PoS networks. These block producers are responsible for regularly aggregating pending transactions into blocks, which are then validated by the entire network and appended to the global ledger. While blockchain networks ensure all transactions are valid (e.g. double-spends) and new blocks of transactions are continually produced (preventing downtime), there isn't actually a guarantee that transactions will be ordered in the exact manner they were submitted to the blockchain.


## Related Documents
---
- [[Blockchain Development]]


## See More
---
- [Blockchain Demo](https://andersbrownworth.com/blockchain/blockchain)
- [Blockchain development guide](https://github.com/dcbuild3r/blockchain-development-guide)
