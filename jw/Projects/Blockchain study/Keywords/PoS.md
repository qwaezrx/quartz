---
tags:
  - Blockchain
aliases:
  - Proof-of-Stake
  - proof-of-stake
---

_Proof-of-stake_ is a way to prove that validators have put something of value into the network that can be destroyed of they act dishonestly. In [[Ethereum]]'s PoS, validators explicitly stake capital in the form of [[ETH]] into a smart contract on Ethereum. The validator is then responsible for checking that new blocks propagated over the network are valid and occasionally creating and propagating new blocks themselves. If they try to defraud the network (for example by proposing multiple blocks when when they ought to send one or sending conflicting attestations), some or all of their staked ETH can be destroyed.

_Proof-of-stake (POS)_ underlies [[Ethereum]]'s [[Consensus Mechanism]]. Ethereum switched on its proof-of-stake mechanism in 2022.


## Validators
To participate as a validator, a user must deposit 32 ETH into the deposit contract and run three separate pieces of software: 
- _[[Execution client]]_
- _[[Consensus client]]_
- _[[Validator client]]_
On depositing their ETH, the user joins an activation queue that limits the rate of new validators joining the network. Once activated, 
1. validators receive new blocks from peers on the Ethereum network. 
2. The transactions delivered in the block are re-executed to check that the proposed changes to Ethereum's state are valid.
3. Check the signature
4. Sends a vote (called an attestation) in favor of that block across the network.

Timing of blocks in:
- [[PoW]]: determined by mining difficulty
- [[PoS]] Ethereum: divided into _slots_ (12 seconds) and _epochs_ (32 slots).
One validator is randomly selected to be a block proposer in every slot. This validator is responsible for creating a new block and sending it out to other nodes on the network. Also in every _slot_, a committee of validators is randomly chosen, whose votes are used to determine the validity of the block being proposed.
Dividing the validator set up into committees is important for keeping the network load manageable. Committees divide up the validator set so that every active validator attests in every epoch, but not in every slot.

## How a transaction gets executed in Ethereum PoS
The following provides an end-to-end explanation of how a [[Transaction]] gets executed in Ethereum PoS.
1. A user creates and signs a [[Transaction]] with their private key.
2. The transaction is submitted to an Ethereum [[Execution client]] which verifies its validity.
3. If the transaction is valid, the execution client adds it to its local [[Mempool]] (list of pending transactions) and also broadcasts it to other nodes over the execution layer gossip network.
	1. Other [[Node|nodes]] hear about the transaction and add it to their local mempool too.

> [!note]
> Advanced users might refrain from broadcasting their transaction and instead forward it to specialized block builders such as [[Flashbots Auction]]. This allows them to organize the transactions in upcoming blocks for maximal profit ([[MEV]]).

4. One of the nodes on the network is the block proposer for the current _slot_, having previously been selected pseudo-randomly using [[RANDAO]]. This node is responsible for building and broadcasting the next block to be added to the Ethereum blockchain and updating the global state. The node is made up of three parts:
	- [[Execution client]]
		1. The _execution client_ bundles transactions from the local mempool into an "__execution payload__"
		2. executes them locally to generate a state change.
		3. This information is passed to the _consensus client_
	- [[Consensus client]]
		1. execution payload is wrapped as part of a "__beacon block__" that also contains information about rewards, penalties, slashing, attestations etc. that enables the network to agree on the sequence of blocks at the head of the chain. The communication between the execution and consensus clients is described in more detail in [Connecting the Consensus and Execution Clients](https://ethereum.org/en/developers/docs/networking-layer/#connecting-clients).
	- [[Validator client]]
5. Other nodes receive the new "__beacon block__" on the consensus layer gossip network. They pass it to their _execution client_ where the transactions are re-executed locally to ensure the proposed state change is valid.
	1. [[Validator client]]
		1. attests that the block is valid and is the logical next block in their view of the chain
			- (meaning it builds on the chain with the greatest weight of attestations as defined in the [fork choice rules](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/#fork-choice)).
	2. The block is added to the local database in each node that attests to it.
6. The transaction can be considered "finalized" if it has become part of a chain with a "__supermajority link__" between two checkpoints. 
	1. Checkpoints occur at the start of each epoch and they exist to account for the fact that only a subset of active validators attest in each slot, but all active validators attest across each epoch. 
		- Therefore, it is only between _epochs_ that a "__supermajority link__" can be demonstrated (this is where 66% of the total staked ETH on the network agrees on two checkpoints).

## Pros and Cons of PoS

| Pros                                                                                                                                                                                                                | Cons                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Staking makes it easier for individuals to participate in securing the network, promoting decentralization. validator node can be run on a normal laptop. Staking pools allow users to stake without having 32 ETH. | Proof-of-stake is younger and less battle-tested compared to [[PoW]]        |
| Staking is more decentralized. Economies of scale do not apply in the same way that they do for PoW mining.                                                                                                         | Proof-of-stake is more complex to implement than PoW                        |
| PoS offers greater crypto-economic security than PoW                                                                                                                                                                | Users need to run three pieces of software to participate in Ethereum's PoS |
| Less issuance of new ETH is required to incentivize network participants                                                                                                                                                                                                                    |                                                                             |

## Comparison to PoW
- better energy efficiency
- lower barriers to entry, reduced hardware requirements
- reduced centralization risk
- because of low energy requirement less ETH issuance is required to incentivize participation
- economic penalties for misbehavior make 51% style attacks more costly for an attacker compared to [[PoW]]
- the community can resort to social recovery of an honest chain if a 51% attack were to overcome the crypto-economic defenses.

## Resources
- https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/


## Read More
- [Proof of Stake FAQ](https://vitalik.ca/general/2017/12/31/pos_faq.html) _Vitalik Buterin_
- [What is Proof of Stake](https://consensys.net/blog/blockchain-explained/what-is-proof-of-stake/) _ConsenSys
- [Video: Vitalik buterin explains proof-of-stake to Lex Fridman](https://www.youtube.com/watch?v=3yrqBG-7EVE)
- [What Proof of Stake Is And Why It Matters](https://bitcoinmagazine.com/culture/what-proof-of-stake-is-and-why-it-matters-1377531463) _Vitalik Buterin_
- [Why Proof of Stake (Nov 2020)](https://vitalik.ca/general/2020/11/06/pos2020.html) _Vitalik Buterin_
- [Proof of Stake: How I Learned to Love Weak Subjectivity](https://blog.ethereum.org/2014/11/25/proof-stake-learned-love-weak-subjectivity/) _Vitalik Buterin_
- [Proof-of-stake Ethereum attack and defense](https://mirror.xyz/jmcook.eth/YqHargbVWVNRQqQpVpzrqEQ8IqwNUJDIpwRP7SS5FXs)
- [A Proof of Stake Design Philosophy](https://medium.com/@VitalikButerin/a-proof-of-stake-design-philosophy-506585978d51) _Vitalik Buterin_
- [Video: Vitalik buterin explains proof-of-stake to Lex Fridman](https://www.youtube.com/watch?v=3yrqBG-7EVE)