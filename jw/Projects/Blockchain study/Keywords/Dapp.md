---
aliases:
  - Decentralized Apps
  - dapps
  - DApps
  - DApp
tags:
  - Blockchain
---

A _decentralized application (dapp)_ is an application built on a decentralized network that combines a [[Smart Contract]] and a frontend user interface. On Ethereum, smart contracts are accessible and transparent - like open APIs - so your dapp can even include a smart contract that someone else has written.


## Dapp

Backend code of:
- _dapp_: runs on a decentralized peer-to-peer network
- _app_: runs on centralized servers.

A dapp can have frontend code and user interfaces written in any language (just like an app) to make calls to its backend. Furthermore, its frontend can get hosted on decentralized storage such as [[IPFS]].
- __Decentralized__ - dapps operate on Ethereum, an open public decentralized platform where no one person or group has control
- __Deterministic__ - dapps perform the same function irrespective of the environment in which they get expected
- __Turing complete__ - dapps can perform any action given the required resources
- __Isolated__ - dapps are executed in a virtual environment known as [[EVM]] so that if the [[Smart Contract]] has a bug, if won't hamper the normal functioning of the blockchain network

_User interfaces for Dapps are hosted on the internet and are built with traditional web technologies._

__Dapp usual flow__:
In order to interact with a smart contract:
1. user needs to submit a request to a server that hosts an application
2. application needs to create a transaction
3. get the signature from a user via a [[Web3]] wallet like [[Metamask]]
4. submit the transaction to an Ethereum RPC.
5. Transaction goes to the [[Mempool|mempool]]
6. gets picked up by a miner/validator
7. gets executed and included in the blockchain
8. User interface update once the blockchain emits an event with a successful call of a function inside of a smart contract.

_You can think of web3 as adding a native value layer to the internet_


## On Smart Contracts

A dapp's backend for lack of a better term. For a detailed overview, head to our section on [[Smart Contract|smart contracts]].

## Benefits of Dapp Development

- __Zero downtime__ - Once the smart contract is deployed on the blockchain, the network as a whole will always be able to serve clients looking to interact with the contract. Malicious actors, therefore, cannot launch denial-of-service attacks targeted towards individual dapps.

- __Privacy__ - You don't need to provide real-world identity to deploy or interact with a dapp

- __Resistance to censorship__ - No single entity on the network can block users from submitting transactions, deploying dapps, or reading data from the blockchain.

- __Complete data integrity__ - Data stored on the blockchain is immutable and indisputable, thanks to cryptographic primitives. Malicious actors cannot forge transactions or other data that has already been made public.

- __Trustless computation/verifiable behavior__ - Smart contracts can be analyzed and are guaranteed to execute in predictable ways, without the need to trust a central authority. This is not true in traditional models; for example, when we use online banking systems, we must trust that financial institutions will not misuse our financial data, tamper with records, or get hacked.

## Drawbacks of Dapp Development

- __Maintenance__ - Dapps can be harder to maintain because the code and data published to the blockchain are harder to modify.
	- It's hard for developers to make updates to their dapps (or the underlying data stored by a dapp) once they are deployed, even if bugs or security risks are identified in an old version.

- __Performance overhead__ - There is a huge performance overhead, and scaling is really hard. To achieve the level of security, integrity, transparency, and reliability that Ethereum aspires to, every node runs and stores every transaction.

- __Network congestion__ - When one dapp uses too many computational resources, the entire network gets backed up. Currently, the network can only process about 10-15 transactions per second; if transactions are being sent in faster than this, the pool of unconfirmed transactions can quickly balloon.

- __User experience__ - It may be harder to engineer _user-friendly_ experiences because the average end-user might find it too difficult to set up a _tool stack_ necessary to interact with the blockchain in a truly secure fashion.

- __Centralization__ - User-friendly and developer-friendly solutions built on top of the base layer of Ethereum might end up looking like centralized services anyways. For example:
	- such services may store keys or other sensitive information server-side
	- serve a frontend using a centralized server
	- or run important business logic on a centralized server before writing to the blockchain.

## Dapps Examples
---

## Resources
---
- https://ethereum.org/en/dapps/#beginner
## See More
- https://ethereum.org/en/developers/docs/dapps/