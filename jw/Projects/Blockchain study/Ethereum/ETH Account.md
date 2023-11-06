---
tags:
  - Blockchain
aliases:
  - ETH accounts
---

An _Ethereum account_ is an entity with an Ether ([[ETH]]) balance that can send transactions on [[Ethereum]]. Accounts can be user-controlled or deployed as [[Smart Contract|smart contracts]].

## Account Types

Ethereum has two account types:
1. [[EOA]] - controlled by anyone with the private keys
2. [[Contract account]] - a smart contract deployed to the network, controlled by code. Learn about [[Smart Contract|smart contracts]]

Both account types has ability to:
- Receive, hold and send ETH and tokens.
- Interact with deployed smart contracts.

### Key differences
#### Externally-owned account(EOA)
- Creating an account costs nothing
- Can initiate transactions
- Transactions between externally-owned accounts can only be ETH/token transfers
- Made up of a cryptographic pair of keys: public and private keys that control account activities

#### Contract account
- Creating a contract has a cost because you're using _network storage_
- Can only send transactions in response to __receiving__ a transaction
- Transactions from an external account to a contract account can trigger code which can execute many different actions, such as:
	- transferring tokens
	- or even creating a new contract
- Contract accounts don't have private keys. Instead, they are controlled by the logic of the __smart contract code__

## Ethereum Account Structure
Ethereum accounts have four fields:
#### Nonce
A counter that indicates the number of transactions sent from an [[EOA|externally-owned account]]. Only one transaction with given nonce can be executed for each account, protecting against replay attacks where signed transactions are repeatedly broadcast and re-executed.
#### Balance
The number of wei owned by this address. Wei is a domination of ETH and there are 1e+18 wei per ETH.
#### CodeHash
This hash refers to the code of an account on the [[EVM]]. Contract accounts have code fragments, programmed in that can perform different operations. This EVM code gets executed if the account gets a message call. It cannot be changed, unlike the other account fields. All such code fragments are contained in the state database under their corresponding hashes for later retrieval. This hash value is known as codeHash. For [[EOA|externally-owned account]], the codeHash field is the hash of an empty string.
#### StorageRoot
Sometimes known as a _storage hash_, A 256-bit hash of the root node of a Merkle Patricia trie that encodes the storage contents of the account (a mapping 256-bit integer values), encoded into the trie as a mapping from the Keccak 256-bit hash of the 256-bit integer keys to the RLP-encoded 256-bit integer values. This trie encodes the hash of the storage contents of this account, and is empty by default.

![Diagram adapted from Ethereum EVM illustrated](https://ethereum.org/static/19443ab40f108c985fb95b07bac29bcb/302a4/accounts.png)


## Resource
- https://ethereum.org/en/developers/docs/accounts/