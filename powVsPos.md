## Concept of Proof of Stake (PoS) vs Proof of Work (PoW)

This post will mainly dig into the differences between PoS and PoW, their benefits, trade-offs.
Since we are expecting a surge of new users once Proof of stake establishes itself, the goal of this post is to keep it simple and to use as few buzzwords as possible.

All of the mentioned concepts (PoS, Pow) are [consensus](https://en.wikipedia.org/wiki/Wikipedia:What_is_consensus) mechanisms, and are a requirement to process transactions without a [middleman](https://www.investopedia.com/terms/m/middleman.asp) (e.g., a Bank) on the blockchain.

### Proof of Work (PoW)

Proof of Work itself was already known since 1993 to prevent DoS attacks and spam on a network by requiring processing time by the computer. In combination with PoW an unknown developer named Satoshi Nakamoto solved a computer science problem called “Byzantine Generals problem” which allowed her/him to **introduce Bitcoin in 2009**.

#### How does it work?

First of all we need to know that users can send each other digital tokens (transactions) which are put together into blocks as seen in the image below.

![blocks&transactions](https://user-images.githubusercontent.com/26490734/78656198-53ebaa80-78c7-11ea-96f9-ed2e35a35b12.png)
###### [image source](https://medium.com/coinmonks/the-bitcoin-blockchain-a3eb996f7140)


With PoW, miners compete against each other to mine the next block. Miners use computation power (=hashing power) to solve very complex math puzzles (e.g., Hash-functions). Apart from this, the complexity to mine increases the more miners join this competition.
However, there’s an **incentive required** to do so: For each mined block the miner gets a reward, the block reward.
As of now bitcoin miners are rewarded with 12.5 Bitcoins per block – roughly 10 minutes per block.

![BlockchainOverview](https://user-images.githubusercontent.com/26490734/78658059-fb69dc80-78c9-11ea-8848-8d73b97e872f.png)
###### [image source](https://waytomine.com/what-is-proof-of-work/)


