## Concept of Proof of Stake (PoS) vs Proof of Work (PoW)

This post will mainly dig into the differences between PoS and PoW, their benefits, trade-offs.
Since we are expecting a surge of new users once Proof of stake establishes itself, the goal of this post is to keep it simple and to use as few buzzwords as possible.

All of the mentioned concepts (PoS, Pow) are [consensus](https://en.wikipedia.org/wiki/Wikipedia:What_is_consensus) mechanisms, and are a requirement to process transactions without a [middleman](https://www.investopedia.com/terms/m/middleman.asp) (e.g., a Bank) on the blockchain.

### Proof of Work (PoW)

Proof of Work itself was already known since 1993 to prevent DoS attacks and spam on a network by requiring processing time by the computer. In combination with PoW an unknown developer named Satoshi Nakamoto solved a computer science problem called “Byzantine Generals problem” which allowed her/him to **introduce Bitcoin in 2009**.

#### <ins>How does it work?</ins>

First of all we need to know that users can send each other digital tokens (transactions) which are put together into blocks as seen in the image below.

![blocks&transactions](https://user-images.githubusercontent.com/26490734/78656198-53ebaa80-78c7-11ea-96f9-ed2e35a35b12.png)
###### [image source](https://medium.com/coinmonks/the-bitcoin-blockchain-a3eb996f7140)

With PoW, miners compete against each other to mine the next block. Miners use computation power (=hashing power) to solve very complex math puzzles (e.g., Hash-functions). Apart from this, the complexity to mine increases the more miners join this competition.
However, there’s an **incentive required** to do so: For each mined block the miner gets a reward, the block reward.
As of now bitcoin miners are rewarded with 12.5 Bitcoins per block – roughly 10 minutes per block.

![BlockchainOverview](https://user-images.githubusercontent.com/26490734/78658059-fb69dc80-78c9-11ea-8848-8d73b97e872f.png)
###### [image source](https://waytomine.com/what-is-proof-of-work/)

#### <ins>Why is all of this so complicated?</ins>

As mentioned in the introduction, PoW enabled a decentralized system which made DoS attacks (almost) impossible since the costs are too high and the incentives to use the required computation power in an honest way is given. 
In this case, Bitcoin, also allows users independently of how much money they own, to participate in the network and mine Bitcoin. 

**Computation power is what matters.**

#### <ins>Weaknesses of PoW</ins>

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

#### <ins>Benefits of PoW</ins>

Due to the fact that Bitcoin was the first ever cryptocurrency, PoW has been the most tested consensus algorithm. The key advantages of PoW are the following:

1. (Almost) impossible to Ddos Attack
2. Extrinsic commitment, miner’s need to burn electricity, which needs to be paid in the local currency. 
    -> Attacking the network costs “real world money”.
3. No barriers, anyone with computation power can participate
4. Rich doesn’t necessarily get richer
5. Proof-of- **work** , requires (expensive) effort in the real world, which can network make attacks expensive.

## Proof of Stake (PoS)

Proof of stake was introduced back in 2011 on the [bitcointalk forum](https://bitcointalk.org/index.php?topic=27787.0) 
Before we start off, it’s important to acknowledge that there are different implementations of PoS, but they are all similar. 

**All of them put money into stake**

#### <ins>How does it work?</ins>

PoS uses a pseudo random election process to choose one of the available nodes to be the next block proposer (=validator) and process the next block. In order to be one of the chosen nodes, coin holders need to lock up their coins (=stake) into the network. By increasing the stake, the odds of being a chosen node also increases and so does the total block reward.
Obviously, the consensus algorithm **shouldn’t** always favour the wealthiest nodes all the time. Therefore, current PoS systems take different criteria into account.

#### <ins>Block selection types</ins>

##### Randomised block selection

The system chooses a node with a combination of the highest stake and lowest hash value. In public blockchains these information are known to the public, therefore the next node can be predicted.

##### Coin Age Method

This model chooses a node based on how long it has been staking for.
The calculation is simple: **(Number of coins) x (Number of days staked)**. 
Once a node has been chosen, the coin age is set back to 0. This prevents huge stake holders from continuously having the highest priority. If an honest staker decides to stop validating blocks, they will receive all of their staked coins and additionally their belonging block rewards.

**Security in PoS:**
The locked stake is a motivator to **not** act maliciously. In case of an malicious attack, the attacker will lose a part or even all of his stake. **If the rewards are higher than the attack costs**, the incentives are given to not attack the network. Like PoW, a successful attack would require 51% of the circulating supply.

#### <ins>Ethereum 2.0 and Proof of Stake</ins>

As of now, Ethereum is running the PoW consensus algorithm, but plans to move to Proof of stake in the near future.
The Ethereum 2.0 research team modified the PoS algorithm slightly, which was required to perform the transition from PoW to Pos.
 
Since Ethereum 2.0 has not shipped yet, it is hard to say whether these modifications turned out in favor or not. Some of these changes are covered in our [glossary](https://kb.beaconcha.in/glossary).
The main idea stays the same. Coins get locked.

*Benefits and weaknesses will be listed in the [“DPoS” section](https://github.com/Buttaa/eth2-knowledge-base/blob/master/powVsPos.md#delegated-proof-of-stake-dpos).*

## Delegated Proof of Stake (DPoS)

The DPoS consensus algorithm was invented in 2014 by a developer called Daniel Larimer and implemented in his project “EOS”. It’s an modification to the PoS idea.

#### <ins>How does it work?</ins>

In this specific case we are going to refer to the EOS network.
EOS-coin holders are maintaining the system by an election system. Coin holders have the ability to vote for delegates and give them the power to validate new blocks, process transactions and earn block rewards. The number of delegates (=witnesses) is restricted to 21 entities.The power each witness gets is proportional to the amount of coins they have been voted with.

These witnesses have the choice to forward their votes to another witness, who are then able to vote on their behalf.
In other words, if Witness_X has the voting power of 5 and Witness_Y the power of 10, Witness_X can hand his votes over to Witness_Y who then has 15.

**Processing blocks and transactions:**

Delegates take turns in validating blocks, process a new block every 2 seconds and each delegate is scheduled for a specific time slot. If a block producer acts maliciously, they lose their reputation and can be replaced by a new block producer.

#### <ins>Weaknesses of (D)PoS</ins>

If we look at the EOS voting statistics it is clear that the majority of the votes are being done from and by centralized exchanges. Which leads to the main arguments:

1. Delegates can easily form cartels
2. Rich get richer
3. Intrinsic commitment system, The network could have attack vector’s which allow them to lose the coins themselves,
    but gain more of them by attacking
4. Users who leave their coins on exchanges [empower exchanges unknowingly](https://www.coindesk.com/why-crypto-should-care-about-justin-suns-steem-drama)

![eosBlockproducerRankings](https://user-images.githubusercontent.com/26490734/78664339-1b060280-78d4-11ea-98ec-178f830569fa.png)
###### [image source](https://eosauthority.com/producers_chart?network=eos#producer-rankings)

#### <ins>Differences between PoW and (D)PoS</ins>

The way these consensus algorithms work have been discussed above and is required to understand the differences.
Proof of work provides security to the network by an investment of energy, which means that miners need to connect their devices and burn electricity.
Compared to PoW, PoS runs lightweight computers to check the rules of the network and validate the transactions.

![PoW_vs_Pow](https://user-images.githubusercontent.com/26490734/78664983-6076ff80-78d5-11ea-9a24-11448ee0c7f4.png)

The list for sure doesn’t stop here; Ethereum 2.0 claims to solves some of the “potential centralization” points and scalability issues. 
This is an ongoing process and will be updated once Ethereum 2.0 launches and stress tested.


![PoW_PoS_Overview](https://user-images.githubusercontent.com/26490734/78665293-e09d6500-78d5-11ea-8f8d-eb310c3b7ab6.png)

[image source](https://blockgeeks.com/guides/proof-of-work-vs-proof-of-stake/)


<ins>*General sources*</ins>

*[Bitcoin Wikipedia](https://en.bitcoinwiki.org/wiki/Proof-of-stake)*

*[Binance Academy](https://www.binance.vision/blockchain)*

*[Andreas Antonopoulos](https://youtu.be/3W_3AQrQEOM)*





























