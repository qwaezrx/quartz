---
aliases:
  - Maximal Extractable Value
  - Miner Extractable Value
  - MEV extraction
tags:
  - Blockchain/MEV
---


_Maximal extractable value (MEV)_ refers to the maximum value that can be extracted from block production in excess of the standard block reward and gas fees by including, excluding, and changing the order of transactions in a block.

>[!Miner Extractable Value]
>MEV was first applied in the context of [[PoW]], and initially referred to as "__miner extractable value__". This is because in proof-of-work, miners control transaction inclusion, exclusion, and ordering. However, since the transition to [[PoS]] in [[Ethereum]], via [[The Merge]] validators have been responsible for these roles, and mining is no longer part of the [[Ethereum]] protocol. The value extraction methods still exist, though, so the term "__Maximal extractable value__" is now used instead.


<iframe width="560" height="315" src="https://www.youtube.com/embed/F9IuBZGseFQ?si=cs6-Qv-lOqAjfHPO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


## How does MEV Work?
---

Since each [[Block]] can only contain a limited number of [[Transaction|transactions]], block producers have full autonomy in selecting which pending transactions in the [[Mempool|mempool]] they will include in their block. While block producers by default order transactions by the highest [[Gas and Fees|gas fee]] (transaction fee) in order to maximize their profits, this is not a requirement by the network. As a result, block producers can extract additional value by taking advantage of their ability to arbitrarily reorder transactions, creating what is known as __MEV__.
![[How_does_MEV_Work?.png]]

Due to the resources and expertise required to extract MEV, it is common for block producers in blockchain networks to outsource the creation of blocks to third-party networks consisting of __searchers__, __builders__, and __relayers__.

MEV often comes at the expense of regular users, many times in ways that may not be immediately apparent to all users until after their transaction is processed. This can include worse price execution for user trades, where MEV is directly extracted from users.

![[MEV_searcher_order_flow_post_merge.png]]
## MEV Extraction
---
In theory MEV extraction accrues entirely to validators because they are the only party that can guarantee the execution of a profitable MEV opportunity. In practice, however, a large portion of MEV is extractable by independent network participants referred to as "__searchers__". Searchers can run complex algorithms on blockchain data to detect profitable MEV opportunities and have bots to automatically submit those profitable transactions to the network.

Validators do get a portion of the full MEV amount anyway because searchers are willing to pay high gas fees (which go to the validator) in exchange for higher likelihood of inclusion of their profitable transactions in a block. Assuming searchers are economically rational, the gas fee that a searcher is willing to pay will be an amount up to 100% of the searcher's MEV (because if the gas fee was higher, the searcher would lose money).

With that, for some highly competitive MEV opportunities, such as [[#DEX arbitrage]], searchers may have to pay 90% or even more of their total MEV revenue in gas fees to the validator because so many people want to run the same profitable arbitrage trade. This is because the only way to guarantee that their arbitrage transaction runs is if they submit the transaction with the highest gas price.

### Gas Golfing
This dynamic has made being good at "__gas golfing__" - programming transactions so that they use the least amount of gas - a competitive advantage, because it allows searchers to set a higher gas price while keeping their total gas fees constant (since _gas fees = gas price * gas used_).

A few well-known gas golfing techniques include: using addresses that start with a long string of zeroes (e.g. [0x0000000000C521824EaFf97Eac7B73B084ef9306](https://etherscan.io/address/0x0000000000c521824eaff97eac7b73b084ef9306)) since they take less space (and hence gas) to store; and leaving small [[ERC-20]] token balances in contracts, since it costs more gas to initialize a storage slot (the case if the balance is 0) than to update a storage slot.Finding more techniques to reduce gas usage is an active area of research among searchers.

### Generalized Frontrunners
Rather than programming complex to detect profitable MEV opportunities, some searchers run generalized frontrunners. ___Generalized frontrunners__ are bots that watch the [[Mempool|mempool]] to detect profitable transactions_. The frontrunner will copy the potentially profitable transaction's code, replace addresses with the frontrunner's address, and run the transaction locally to double-check that the modified transaction results in a profit to the frontrunner's address. If the transaction is indeed profitable, the frontrunner will submit the modified transaction with the replaced address and a higher gas price, "__frontrunning__" the original transaction and getting the original searcher's MEV.

### Flashbots
[[Flashbots|Flashbots]] is an independent project which extends execution clients with a service that allows searchers to submit MEV transactions to validators without revealing them to the public [[Mempool|mempool]]. _This prevents transactions from being frontrun by [[#Generalized Frontrunners]].


## MEV Examples
---
### DEX arbitrage
[[DEX|Decentralized exchange]] (DEX) arbitrage is the simplest and most well-known MEV opportunity. As a result, it is also the most competitive.

It works like this: if two DEXes are offering a token at two different prices, someone can buy the token on the lower-priced DEX and sell it on the higher-priced DEX in a single, atomic transaction. Thanks to the mechanics of the blockchain, this is true, riskless arbitrage.

[Here's an example](https://etherscan.io/tx/0x5e1657ef0e9be9bc72efefe59a2528d0d730d478cfc9e6cdd09af9f997bb3ef4) of a profitable arbitrage transaction where a searcher turned 1,000 ETH into 1,045 ETH by taking advantage of different pricing of the ETH/DAI pair on Uniswap vs. Sushiswap.
### Liquidations
Lending protocol liquidations present another well-known MEV opportunity.

Lending protocol like Maker and Aave require users to deposit some collateral (e.g. ETH). This deposited collateral is then used to then lend out to other users.

Users can then borrow assets and tokens from others depending on what they need (e.g. you might borrow MKR if you want to vote in a MakerDAO governance proposal) up to a certain percentage of their deposited collateral. For example, if the borrowing amount is a maximum of 30%, a user who deposits 100 DAI into the protocol can borrow up to 30 DAI worth of another asset. The protocol determines the exact borrowing power percentage.

As the value of a borrower's collateral fluctuates, so too does their borrowing power. If, due to market fluctuations, the value of borrowed assets exceeds say, 30% of the value of their collateral (again, the exact percentage is determined by the protocol), the protocol typically allows anyone to liquidate the collateral, instantly paying off the lenders (this is similar to how _margin calls_ work in traditional finance). If liquidated, the borrower usually has to pay a hefty liquidation fee, some of which goes to the liquidator - which is where the MEV opportunity comes in.

Searchers compete to parse blockchain data as fast as possible to determine which borrowers can be liquidated and be the first to submit a liquidation transaction and collect the liquidation fee for themselves.

### Sandwich Trading
Sandwich trading is another common method of MEV extraction.

To sandwich, a searcher will watch the mempool for large DEX trades. For instance, suppose someone wants to buy 10,000 UNI with DAI on Uniswap. A trade of this magnitude will have a meaningful effect on the UNI/DAI pair, potentially significantly raising the price of UNI relative to DAI.

A searcher can calculate the approximate price effect of this large trade on the UNI/DAI pair and execute an optimal buy order immediately before the large trade, buying UNI cheaply, then execute a sell order immediately after the large trade, selling it for the higher price caused by the large order.

Sandwiching, however, is riskier as it isn't atomic (unlike DEX arbitrage, as described above) and is prone to a [[Salmonella Attack]]

### NFT MEV
MEV in the NFT space is an emergent phenomenon, and isn't necessarily profitable.

However, since NFT transactions happen on the same blockchain shared by all other Ethereum transactions, searchers can use similar techniques as those used in traditional MEV opportunities in the NFT market too.

For example, if there's a popular NFT drop and a searcher wants a certain NFT or set of NFTs, they can program a transaction such that they are the first in line to buy the NFT, or they can buy the entire set of NFTs in a single transaction. Or if an NFT is  [mistakenly listed at a low price](https://www.theblockcrypto.com/post/113546/mistake-sees-69000-cryptopunk-sold-for-less-than-a-cent), a searcher can frontrun other purchasers and snap it up for cheap.

One prominent example of NFT MEV occurred when a searcher spent $7M to buy every single Cryptopunk at the price floor. A blockchain researcher explained on Twitter how the buyer worked with an MEV provider to keep their purchases secret.

### The long tail
DEX arbitrage, liquidations, and sandwich trading  are all very well-known MEV opportunities and are unlikely to be profitable for new searchers. However, there is a long tail of lesser known MEV opportunities (NFT MEV is arguably one such opportunity).

Searchers who are just getting started may be able to find more success by searching for MEV in this longer tail. Flashbot's [MEV job board](https://github.com/flashbots/mev-job-board) lists some emerging opportunities.

## State of MEV
---
MEV extraction ballooned in early 2021, resulting in extremely high gas prices in the first few months of the year. The emergence of [[Flashbots|Flashbots]]'s MEV relay has reduced the effectiveness of _generalized frontrunners_ and has taken gas price auctions off-chain, lowering gas prices for ordinary users.

While many _searchers_ are still making good money from MEV, as opportunities become more well-known and more and more searchers compete for the same opportunity, validators will capture more and more total MEV revenue. MEV is not unique to [[Ethereum]], and as opportunities become more competitive on Ethereum, searchers are moving to alternative blockchains like [[BSC]], where similar MEV opportunities as those on Ethereum exist with less competition.

On the other hand, the transition from PoW to PoS and the ongoing effort to scale Ethereum using rollups all change the MEV landscape in ways that are still somewhat unclear. It is not yet well known how having guaranteed block-proposers known slightly in advance changes the dynamics of MEV extraction compared to the _probabilistic model in PoW_ or how this will be disrupted when [[Single Secret Ledger Election|single secret ledger election]] and [[DVT|distributed validator technology]] get implemented. Similarly, it remains to be seen what MEV opportunities exist when most user activity is ported away from Ethereum and onto its layer 2 rollups and shards.

### MEV Future
- __MEV-boost__
- __The Scourge__: __MEV-burn__
	- burning extracted MEVs
![[The_Scourge_roadmap.png]]
- __MEV-share__
- __Committee-driven MEV-smoothing__
![[Pasted image 20231031070006.png]]
- __Shutterized Beacon Chain__
- __Encrypted Mempool__


## MEV in Different Chains
---
- [[MEV in Ethereum PoS]]


## Resources
---
- https://ethereum.org/en/developers/docs/mev/
- [What Is Miner-Extractable Value (MEV)?](https://blog.chain.link/what-is-miner-extractable-value-mev/)
- https://github.com/flashbots/mev-job-board
- [MEV-Explore](https://explore.flashbots.net)

### Courses
- https://www.udemy.com/course/full-ethereum-node-mempool/

## See More
---
- [MEV and Me](https://www.paradigm.xyz/2021/02/mev-and-me)
- [Ethereum is a Dark Forest](https://www.paradigm.xyz/2020/08/ethereum-is-a-dark-forest/)
- [Escaping the Dark Forest](https://samczsun.com/escaping-the-dark-forest/)
- [Flashbots: Frontrunning the MEV Crisis](https://medium.com/flashbots/frontrunning-the-mev-crisis-40629a613752)
- [@bertcmiller's MEV Threads](https://twitter.com/bertcmiller/status/1402665992422047747)
- [MEV-Boost: Merge ready Flashbots Architecture](https://ethresear.ch/t/mev-boost-merge-ready-flashbots-architecture/11177)
- [What Is MEV Boost](https://www.alchemy.com/overviews/mev-boost)
- [Why run mev-boost?](https://writings.flashbots.net/writings/why-run-mevboost/)
- [The Hitchhikers Guide To Ethereum](https://members.delphidigital.io/reports/the-hitchhikers-guide-to-ethereum)