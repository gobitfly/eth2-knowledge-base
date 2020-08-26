---
description: Attestation inclusion delay and they are important
---

# Attestation Rewards

## Rewards

The attestation reward is dependent on two variables, the [**base reward**](https://github.com/ethereum/eth2.0-specs/blob/dev/specs/phase0/beacon-chain.md#constants) and the **inclusion delay.**

![Source: ConsenSys Codefi Analysis](../.gitbook/assets/image%20%28165%29.png)

#### **Base reward**

**\(**Validator effective balance**\)** **/ \(**Effective balance of **all** active validators**\)** \* **\(**2\*\*6**\)**

#### Inclusion delay

At the time when the validators voted on the head of the chain \(Block 0\), Block 1 was not proposed yet.  
Therefore attestations naturally get included **one block** later; so all attestations who voted on Block 0 being the chain head got included in Block 1 and the **inclusion delay** is 1.

![](../.gitbook/assets/image%20%28162%29.png)

##  **What if the voting validator, all aggregators and/or the block proposer are missing?**

#### \*\*\*\*

#### **Missing Voting Validator**

These validators have a maximum of 1 epoch to submit their attestation. If the attestation was missed in epoch 0, they can submit it with an inclusion delay in epoch 1.

####  Missing Aggregator

There are 16 Aggregators per epoch in total, additionally random validators from the beaconchain subscribe to **two subnets for 256 Epochs** and serve as a backup in case aggregators are missing.

![](../.gitbook/assets/image%20%28167%29.png)

#### Missing block proposer

Lucky aggregegators can also be chosen to be the block proposer. If the attestation was not included because the block proposer has gone missing, the next block proposer will pick them up but the **inclusion delay** will increase by one.  


## Beaconcha.in Explorer & Inclusion delay

![](../.gitbook/assets/image%20%28166%29.png)

