---
description: Attestation inclusion delay explained
---

# Attestation Rewards

## Rewards

The attestation reward is dependent on two variables, the [**base reward**](https://github.com/ethereum/eth2.0-specs/blob/dev/specs/phase0/beacon-chain.md#constants) and the **inclusion delay.  
The best case for the inclusion delay is to be 1.**

![Source: ConsenSys Codefi Analysis](../.gitbook/assets/image%20%28165%29.png)

#### **Base reward**

**\(**Validator effective balance \* 2\*\*6**\)** **/ SQRT\(**Effective balance of **all** active validators**\)** 

#### Inclusion delay

At the time when the validators voted on the head of the chain \(Block 0\), `Block 1` was not proposed yet.  
Therefore attestations naturally get included **one block** later; so all attestations who voted on `Block 0` being the chain head got included in `Block 1` and, the **inclusion delay** is 1.

![](../.gitbook/assets/image%20%28162%29.png)

#### 

#### The effects of the inclusion delay on the attestation reward 

As seen below, an Inclusion delay of 2 causes the the reward to drop by 50%. 

![Source: Consensys](../.gitbook/assets/image%20%28170%29.png)





##  **What if the voting validator, all aggregators and/or the block proposer are missing?**

#### \*\*\*\*

#### **Missing Voting Validator**

These validators have a maximum of 1 epoch to submit their attestation. If the attestation was missed in epoch 0, they can submit it with an inclusion delay in epoch 1.

####  Missing Aggregator

There are 16 Aggregators per epoch in total, additionally, random validators from the beacon-chain subscribe to **two subnets for 256 Epochs** and serve as a backup in case aggregators are missing.

![](../.gitbook/assets/image%20%28169%29.png)

#### Missing block proposer

Note that in some cases a lucky aggregator may also become the block proposer. If the attestation was not included because the block proposer has gone missing, the next block proposer would pick the aggregated attestation up and include it into the next block. However, the **inclusion delay** will increase by one.

## Beaconcha.in Explorer & Inclusion delay

Let's look at the example below.   
The attestation for `slot 156508` was included in `slot 156510` but why is the inclusion distance 0?  
If were to use the formula from above and set the inclusion delay to 0, the rewards would be 0 for a proposed attestation as well.

![](../.gitbook/assets/image%20%28166%29.png)

Technically speaking, there is an inclusion delay of two slots, but since the attestant is not responsible for the block proposal, and to only warn the user about its faults \(e.g. slow internet connection, power failure etc.\), the [beaconcha.in explorer](https://beaconcha.in/) displays the distance as 0.



_Source:_   
[_Attestation Inclusion_](https://www.youtube.com/watch?v=SPcgevcDqDE&feature=youtu.be) _- Adrian Sutton_  


