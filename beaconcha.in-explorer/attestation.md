---
description: An overview of attestations
---

# Attestation

### Attestation&#x20;

Every [Epoch](https://kb.beaconcha.in/glossary#epoch) (\~6.4 minutes) a validator proposes an attestation (vote) to the network.\
This vote consists of the following segments:

* [Committee](https://kb.beaconcha.in/glossary#slots)
* [Validator Index](https://kb.beaconcha.in/glossary#unique-index)
* Finality vote
* Signature
* Chain head vote (vote on what the validator believes is the head of the chain)&#x20;

A minimum of 16,384 validators is required to start Ethereum 2.0\
If we multiply that with the information included in each Attestation per Epoch, it adds up quickly. Therefore, Ethereum 2.0 **aggregates** all of that information and minimises the data growth.\


### Aggregated Attestation

> An [aggregation](https://www.vocabulary.com/dictionary/aggregation) is a collection, or the gathering of things together. Your baseball card collection might represent the aggregation of lots of different types of cards.

So what does that mean for Attestations?\
\
Each block one or more committees are chosen to attest. A committee has a minimum of 128 validators, of which 16 are randomly selected to become an aggregator.\
As shown below, the validators broadcast their unaggregated attestation to the aggregators (red arrow). The aggregators then merge the attestations and forward a single aggregated attestation to the [block proposer](https://github.com/gobitfly/eth2-beaconchain-explorer/pull/218).

### &#x20;Attestation Inclusion Lifecycle &#x20;

1. Generation
2. Propagation
3. Aggregation
4. Propagation
5. Inclusion

![](<../.gitbook/assets/image (184).png>)

### &#x20;Rewards

The attestation reward is dependent on two variables, the [**base reward**](https://github.com/ethereum/eth2.0-specs/blob/dev/specs/phase0/beacon-chain.md#constants) and the **inclusion delay.**\
**The best case for the inclusion delay is to be 1.**

![Source: ConsenSys Codefi Analysis](<../.gitbook/assets/image (84).png>)

#### **Base reward**

**(**Validator effective balance \* 2\*\*6**)** **/ SQRT(**Effective balance of **all** active validators**)**&#x20;

#### Inclusion delay

At the time when the validators voted on the head of the chain (Block 0), `Block 1` was not proposed yet.\
Therefore attestations naturally get included **one block** later; so all attestations who voted on `Block 0` being the chain head got included in `Block 1` and, the **inclusion delay** is 1.

![](<../.gitbook/assets/image (158).png>)

####

#### The effects of the inclusion delay on the attestation reward&#x20;

As shown below, an Inclusion delay of 2 causes the the reward to drop by 50%.&#x20;

![Source: Consensys](<../.gitbook/assets/image (163).png>)

### &#x20;**A**ttestation scenarios&#x20;

**Missing Voting Validator**

These validators have a maximum of 1 epoch to submit their attestation. If the attestation was missed in epoch 0, they can submit it with an inclusion delay in epoch 1.

#### &#x20;Missing Aggregator

There are 16 Aggregators per epoch in total, additionally, random validators from the beacon-chain subscribe to **two subnets for 256 Epochs** and serve as a backup in case aggregators are missing.

![](<../.gitbook/assets/image (172).png>)

#### Missing block proposer

Note that in some cases a lucky aggregator may also become the block proposer. If the attestation was not included because the block proposer has gone missing, the next block proposer would pick the aggregated attestation up and include it into the next block. However, the **inclusion delay** will increase by one.\


_Credits_\
[_Attestation effectiveness_](https://www.attestant.io/posts/defining-attestation-effectiveness/) _-_ [_AttestantIO_](https://twitter.com/attestantio)\
[_Attestation Inclusion_](https://www.youtube.com/watch?v=SPcgevcDqDE\&feature=youtu.be) _-_ [_Adrian Sutton_ ](https://twitter.com/ajsutton)_(Consensys)_\
