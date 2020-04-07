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

#### Why is all of this so complicated?

As mentioned in the introduction, PoW enabled a decentralized system which made DoS attacks (almost) impossible since the costs are too high and the incentives to use the required computation power in an honest way is given. 
In this case, Bitcoin, also allows users independently of how much money they own, to participate in the network and mine Bitcoin. **Computation power is what matters.**

#### Weaknesses of PoW

In order to achieve as much decentralization as possible. The idea is to distribute all of the nodes and miners across the world and to not have a central entity controlling more than 50% of the hashing power.
However, this is harder in practice:
Due to electricity costs, hardware production costs and other factors, some countries are more attractive than others. China is one of them, they currently control a very large size of the hashing power.
As of today, four mining pools are required to coordinate a 51% attack to the Bitcoin network. (51% of the total hashing power)

![bitcoinMiningPools](https://user-images.githubusercontent.com/26490734/78660187-f0fd1200-78cc-11ea-992f-f8556a5c549a.png)

[image source](https://btc.com/stats/pool)

An 51% attack would allow those entities to **modify transactions, stop transactions from being confirmed, reverse transactions** and lead to a double spending problem.
**Changing the block rewards, modifying the inflation rate (=creating coins) or stealing coins**, however, **are not possible**.
Changing a certain block (attacking) is only possible if all subsequent confirmed blocks are discarded. This increases the costs of an attack the longer we go back in history.

**As long as the incentives to be honest are higher than the ones to be malicious, the possibility of an 51% attack is extremely low.** Note that such an attack has never been performed on Bitcoin since day one.

To sum up, the main weaknesses about PoW are:

1. energy insensitivity
2. centralization of hashing power
3. potential hardware monopoly
4. Slow transaction speed (Layer 1)

#### Benefits of PoW

Due to the fact that Bitcoin was the first ever cryptocurrency, PoW has been the most tested consensus algorithm. The key advantages of PoW are the following:

1. (Almost) impossible to Ddos Attack
2. Extrinsic commitment, miner’s need to burn electricity, which needs to be paid in the local currency. 
    -> Attacking the network costs “real world money”.
3. No barriers, anyone with computation power can participate
4. Rich doesn’t necessarily get richer
5. Proof-of- **work** , requires (expensive) effort in the real world, which can network make attacks expensive.







