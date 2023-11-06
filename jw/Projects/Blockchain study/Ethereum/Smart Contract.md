---
aliases:
  - smart contracts
  - smart contract
---

_Smart contracts_ are programs that govern the behavior of accounts within the [[Ethereum]] state.

- Smart contracts are a type of [[Ethereum Account|Ethereum accounts]].
	- Meaning that they have a balance and can send [[Transaction|transactions]] over the network.
- Deployed on the network and run as programmed
- [[EOA|EOAs]] can interact with it by submitting transactions that interact with functions that are publicly accessible.
- Can be used to define rules which are enforced via code


## What are Smart Contracts?
---
Developers upload programs (reusable snippets of code) into [[EVM]] state, and users make requests to execute these code snippets with varying parameters. We call the programs uploaded to and executed by the network _smart contracts_.

A script that, when called with certain parameters, performs some actions or computation if certain conditions are satisfied. For example, a simple vendor smart contract could create and assign ownership of a digital asset if the caller sends [[ETH]] to a specific recipient.

Any developer can create a smart contract and make it public to the network, using the blockchain as its data layer, for a fee paid to the network. Any user can then call the smart contract to execute its code, again for a fee paid to the network.

Thus, with smart contracts, developers can build and deploy arbitrary complex user-facing apps and services such as:
- marketplace
- financial instruments
- games
- etc.
These are often called [[Dapp]]


## Related Documents
---
- [[A Simple Smart Contract (Solidity)]]

## See More
---
-  [Remix](https://remix.ethereum.org/)