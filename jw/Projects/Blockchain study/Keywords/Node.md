---
aliases:
  - Nodes
  - node
  - nodes
tags:
  - Blockchain
---

## Typical Modules of a Blockchain Node
---
### Runtime
- Engine or glue of the [[Blockchain|blockchain]]
- [[Smart Contract|smart contract]] execution ([[EVM]])
- [[Transaction]] execution

### Data Storage
- Stores blockchain
- Stores transaction pools
- Stores user wallets
- Stores meta data
- Performs indexing
- Supports data retrieval

### P2P Networking
- Searching for peers
- Connecting to peers
- Broadcasting messages
- Receiving messages
- Maintaining active peer list
- Network protocol implementation
- Essential for decentralization

### Consensus
- [[PoW]]
- [[PoS]]
- Delegated Proof of Stake
- Proof of History
- etc.
Consensus allows production of blocks and thus confirmation of transactions.

### Syncing
- Client vs Network synchronization
- Initial blockchain download
- Ongoing new blocks

### Block Management
- Creation of new blocks
- Validation of new blocks
- Propagation of new blocks

### Wallet Management
- Creating new user addresses
- Signing of transactions
- Managing user balances

### Transaction Management
- [[Transaction]]
	- creation
	- validation
	- propagation
	- pool management

### API
- Interface to interact with client
	- Query transactions
	- Query blockchain state
	- Send transactions
	- Subscribing to events

## See More
---
- https://ethereum.org/en/developers/docs/nodes-and-clients/