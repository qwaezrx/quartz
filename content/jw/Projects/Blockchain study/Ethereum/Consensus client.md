---
aliases:
  - consensus client
  - consensus clients
tags:
  - Blockchain/Ethereum
---

The _consensus client_ deals with all the logic that enables a node to stay in sync with the [[Ethereum]] network. This includes receiving blocks from peers and running a fork choice algorithm to ensure the node always follows the chain with the greatest accumulation of attestations (weighted by validator effective balances). Similar to the [[Execution client]], consensus clients have their own P2P network through which they share [[Block|blocks]] and attestations.

	The consensus client does not participate in attesting to or proposing blocks - this is done by a [[Validator client]], an optional add-on to a consensus client. A consensus client without a validator only keeps up with the head of the chain, allowing the node to stay synced. This enables a user to transact with Ethereum using their execution client, confident that they are on the correct chain.
