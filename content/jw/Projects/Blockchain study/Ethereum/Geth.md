---
tags:
  - Blockchain/Ethereum
aliases:
  - Go-ethereum
---

_Go-ethereum_ (aka Geth) is an [[Ethereum]] client built in [[Go]]. It is one of the original and most popular Ethereum clients.

## Hardware Requirements
---
[Geth Hardware Requirements](https://geth.ethereum.org/docs/getting-started/hardware-requirements)

- CPU core: __4 core__
- Memory: __16GB RAM__
- Disk space: 
	- __2TB SSD (recommended)__
	- >650GB for _snap-synced full node_
		- with default cache size, grows about 14GB/week.
		- Pruning brings the total storage back down to the original 650GB
	- A "full" archive node that keeps all state back to genesis requires more than 12TB of space.
	- Partial archive nodes can also be created by turning off the garbage collector after some sync
		- The storage requirement depends how much state is saved.
- Bandwidth: __25Mbps (at least)__
	- better to use an [[ISP]] that does not have a capped data allowance.


## Getting Started
---
### Install and Build
[Link](https://geth.ethereum.org/docs/getting-started/installing-geth)

__How to install with Docker__: https://about-tech.tistory.com/190

### Connecting to Consensus Clients
[Link](https://geth.ethereum.org/docs/getting-started/consensus-clients)

Geth is an [[Execution client|execution client]].
Geth needs to be coupled to another piece of software called a [[Consensus client|consensus client]].

There are five consensus clients available, all of which connect to Geth in the same way.

A complete command to start Geth so that it can connect to a consensus client:
```sh
geth --authrpc.addr localhost --authrpc.port 8551 --authrpc.vhosts localhost --authrpc.jwtsecret /tmp/jwtsecret
```
#### Consensus Clients
There are currently five consensus clients that can be run alongside Geth. These are:

[Lighthouse](https://lighthouse-book.sigmaprime.io/): written in Rust

[Nimbus](https://nimbus.team/): written in Nim

[Prysm](https://docs.prylabs.network/docs/getting-started/): written in Go

[Teku](https://pegasys.tech/teku): written in Java

[Lodestar](https://lodestar.chainsafe.io/): written in Typescript

It is recommended to consider [client diversity](https://ethereum.org/en/developers/docs/nodes-and-clients/client-diversity) when choosing a consensus client. Instructions for installing each client are provided in the documentation linked in the list above.

The consensus clients all expose a [Beacon API](https://ethereum.github.io/beacon-APIs) that can be used to check the status of the Beacon client or download blocks and consensus data by sending requests using tools such as [Curl](https://curl.se/). More information on this can be found in the documentation for each consensus client.



## Resource
---
- https://geth.ethereum.org/
- https://geth.ethereum.org/docs