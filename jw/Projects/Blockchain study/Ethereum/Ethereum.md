---
tags:
  - Blockchain/Ethereum
aliases:
---


_Ethereum_ is a [[blockchain]] with a computer embedded in it. It is the foundation for building apps and organizations in a decentralized, permissionless, censorship-resistant way.

In the Ethereum universe, there is a single, canonical computer (called the _Ethereum Virtual Machine_, or [[EVM]]) whose state everyone on the Ethereum network agrees on. Everyone who participates in the Ethereum network (every _Ethereum node_) keeps a copy of the state of this computer. Additionally, any participant can broadcast a request for this computer to perform arbitrary computation. Whenever such a request is broadcast, other participants on the network verify, validate, and carry out ("execute") the computation. This execution causes a state change in the EVM, which is committed and propagated through the entire network.

Requests for computation are called _transaction requests_; the record of all transactions and the EVM's present state gets stored on the blockchain, which in turn is stored and agreed upon by all nodes.

Cryptographic mechanisms ensure that once transactions are verified as valid and added to the blockchain, they can't be tampered with later. The same mechanisms also ensure that all transactions are signed and executed with appropriate "permissions" (no one should be able to send digital assets from Alice's account, except for Alice herself).

- Uses [[ETH]] as the native cryptocurrency of Ethereum.


The [[Ethereum]] network began by using a consensus mechanism that involved PoW. This allowed the nodes of the Ethereum network to agree on the state of all information recorded on the Ethereum blockchain and prevented certain kinds of economic attacks. However, Ethereum switched off proof-of-work in 2022 and started using [[PoS]] instead. 

## Ethereum Terminology
#### __[[Blockchain]]__
The sequence of all blocks that have been committed to the Ethereum network in the history of the network.
#### [[ETH]]
_ETH_ is the native cryptocurrency of Ethereum. Users pay ETH to other users to have their code execution requests fulfilled.
#### [[EVM]]
#### [[Node|Nodes]]
The real-life machines which are storing the [[EVM]] state. Nodes communicate with each other to propagate information about the EVM state and new state changes. Any user can also request the execution of code by broadcasting a code execution request from a node. The Ethereum network itself is the aggregate of all Ethereum nodes and their communications.
#### Accounts
Where ETH is stored. Users can initialize accounts, deposit ETH into the accounts, and transfer ETH from their accounts to other users. Accounts and account balances are stored in a big table in the [[EVM]]; they are a part of the overall EVM state.
#### [[Transaction]]
A "__transaction request__" is the formal term for a request for code execution on the EVM, and a "__transaction__" is a fulfilled transaction request and the associated change in the EVM state. Any user can broadcast a transaction request to the network from a node. For the transaction request to affect the agreed-upon EVM state, it must be:
- validated
- executed
- "__committed to the network__" by another node
Execution of any code causes a state change in the EVM; upon commitment, this state change is broadcast to all nodes in the network. Some examples of transactions:
- Send X ETH from my account to Alice's account
- Publish some smart contract code into EVM state
- Execute the code of the smart contract at address X in the EVM, with arguments Y.
#### [[Block]]
#### [[Smart Contract]]


## Resource
- [Intro to Ethereum](https://ethereum.org/en/developers/docs/intro-to-ethereum/#what-is-ether)


## See More
- [Learn by Coding](https://ethereum.org/ko/developers/learning-tools/)
- https://www.youtube.com/playlist?list=PLJz1HruEnenCXH7KW7wBCEBnBLOVkiqIi

- [Ethereum Whitepaper](https://ethereum.org/en/whitepaper/)
- [How does Ethereum work, anyway?](https://www.preethikasireddy.com/post/how-does-ethereum-work-anyway) - _Preethi Kasireddy_ (**NB** this resource is still valuable but be aware that it predates [The Merge](https://ethereum.org/en/roadmap/merge/) and therefore still refers to Ethereum's proof-of-work mechanism - Ethereum is actually now secured using [proof-of-stake](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/))

- [A developer's guide to Ethereum, part 1](https://ethereum.org/en/developers/tutorials/a-developers-guide-to-ethereum-part-one/) _– A very beginner-friendly exploration of Ethereum using Python and web3.py_

