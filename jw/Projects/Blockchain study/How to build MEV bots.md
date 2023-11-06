---
tags:
  - Blockchain/MEV
---


Things to study:
- [[Rust]]
- [[Solidity]]/Yul
- [[Uniswap]]
- [[Flashloans]]
- [[Gas optimization]]
- [[Flashbots]]

## 1. First key to building MEV bots: The simulation engine

How we can effectively search for these opportunities:
1. __Mempool data__: pending transactions
2. __Transaction/Event data__: confirmed transactions

Full implementation of a sandwiching bot written in JS:
- https://github.com/libevm/subway?source=post_page-----c9c0420d2e1--------------------------------
- https://github.com/flashbots/simple-arbitrage?source=post_page-----c9c0420d2e1--------------------------------

We need our own searching bot and simulation engine.
Begin with:
1. __Search__
2. __Simulate__ <<

### Start building simulation bots
- Need to perform [[Multi-hop Swaps]] (a typical n-way arbitrage) across a number of [[DEX]]s using a single chain.
- Want to figure out if the n-way path I found will be profitable if I sent a transaction performing the swaps.

This could be done in 2 ways:
1. By coding your own simulator that has all the price impact functions implemented. ([Why price impact is critical](https://www.paradigm.xyz/2021/04/understanding-automated-market-makers-part-1-price-impact)) -- __time consuming__
	- Need to understand how your swap/trades will affect the pair prices on different DEX protocols by reading their docs and contracts.
		- The difficult part of this is that the _AMM formulas_ these DEXs use all differ from one another.

2. By using [[Smart Contract|smart contracts]] to simulate price impacts.
	- Don't have to understand all formulas in DEXs.
	- Need to figure out what functions DEXs use to simulate their swaps.
		- This information is public and is easily found with some familiarity with [[Solidity]].
	- Calling smart contract functions is free of charge if you are not changing the blockchain state - other than the contract creation fee.

We will try on _2._ first.
#### Project setup
I'll be using [[Foundry]] to write out my smart contract to simulate the potentially profitable swap paths.

Foundry uses [[Rust]] so you will need to have Rust/Cargo installed.
Install Rust and Cargo (Linux and macOS):
```
curl https://sh.rustup.rs -sSf | sh
```

Run the below command to install Foundryup:
```
curl -L https://foundry.paradigm.xyz | bash
```

Then run:
```
foundryup
```

Now that you have the dependencies installed, you can initialize your Foundry project:
```
forge init swap-simulator-v1
cd swap-simulator-v1 && forge build
forge install OpenZeppel in/openzeppelin-contracts
```

In the `src` directory, create a new Solidity file called`SimulatorV1.sol`.

```solidity
// SPDX-License-Identifier: MIT  
pragma solidity ^0.8.9;  
  
import "openzeppelin-contracts/contracts/utils/math/SafeMath.sol";  
  
contract SimulatorV1 {  
using SafeMath for uint256;  
  
// Polygon network addresses  
address public UNISWAP_V2_FACTORY = 0x5757371414417b8C6CAad45bAeF941aBc7d3Ab32;  
address public UNISWAP_V3_QUOTER2 = 0x61fFE014bA17989E743c5F6cB21bF9697530B21e;  
  
struct SwapParams {  
uint8 protocol; // 0 (UniswapV2), 1 (UniswapV3), 2 (Curve Finance)  
address pool; // used in Curve Finance  
address tokenIn;  
address tokenOut;  
uint24 fee; // only used in Uniswap V3  
uint256 amount; // amount in (1 USDC = 1,000,000 / 1 MATIC = 1 * 10 ** 18)  
}  
  
constructor() {}  
  
function simulateSwapIn(SwapParams[] memory paramsArray) public returns (uint256) {  
  
}  
  
function simulateUniswapV2SwapIn(SwapParams memory params) public returns (uint256 amountOut) {  
  
}  
  
function simulateUniswapV3SwapIn(SwapParams memory params) public returns (uint256 amountOut) {  
  
}  
  
function simulateCurveSwapIn(SwapParams memory params) public returns (uint256 amountOut) {  
  
}  
}
```

This is the basic structure of our simulator. We will be using [[Polygon]], because [[Gas and Fees|gas fee]] there is very cheap and, thus, is a good place to test out your code.






Studying [[Geth]] might be the best way to start with MEV.

Bots to build:
- Frontrunning bot
- Sandwiching bot
- Uniswap JIT provisioning bot

Install web3.py
- https://web3py.readthedocs.io/en/latest/quickstart.html

Install Geth
- https://geth.ethereum.org/docs/getting-started/installing-geth


## Resources
---
- [Ethereum for Python developers](https://ethereum.org/ko/developers/docs/programming-languages/python/)

- https://medium.com/@solidquant/i-decided-to-build-my-own-mev-bot-heres-how-i-m-doing-it-74c3419da49a
- https://medium.com/@solidquant/mev-templates-written-in-python-javascript-and-rust-ddd3d324d709