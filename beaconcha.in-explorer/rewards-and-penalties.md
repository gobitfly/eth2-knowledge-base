---
description: The journey of a validator balance
---

# Rewards and Penalties

A simplified overview of the most common validator rewards and penalties

## Epoch

A validator can propose **one attestation** and **one block** per epoch and depending on their properties the reward varies

## Attestation reward

Rewards and penalties are based on the correctness of

* **Source**
* **Head**
* **Target**

**Head, Source, target,** can be either positive or negative, however the **inclusion delay** can just be positive. The **Source** has to be **correct** in order to get included.&#x20;

### Base Reward

![](<../.gitbook/assets/grafik (1).png>)

![](<../.gitbook/assets/image (196) (1).png>)

The **worst** inclusion speed reward is **base\_reward \* 1/32 \* 7/8** with an inclusion distance of 32 and the **best** is **base\_reward \* 1/1 \* 7/8** with an inclusion distance of 1.

### &#x20;**Possible Attestation properties**

![](<../.gitbook/assets/image (179).png>)



### **Common case scenarios**

_Assumption: The participation rate is 100%_

1. You vote correctly and gets included in the next slot: you get **31/8\*base\_reward**
2. You miss head because you got a late block and it gets included in the next slot: **15/8\*base\_reward**
3. You miss head and target cause you got late a block, you get **-1/8\* base\_reward**
4. You attest and vote correctly, but the next block is missed, you get **55/16 \* base\_reward**
5. You attest correctly and get perfect inclusion distance, but you attested on a block that most people got late as in 2., you get **\~7/8 \* base\_reward**\
   \
   &#xNAN;_&#x54;he last one is the most confusing one: When there is a late block where validators miss the head, the validator that misses the head earns **more** than the validator that votes correctly, as in 2._ \
   _15/8 > 7/8_

**Best possible reward**\
31/8 \* base\_reward\
\
**Worst possible reward with an included attestation ("Negative Reward")**\
-249/256 \* base\_reward

## Block reward

Only **valid** attestations (correct source) can be included in a block and the rewards for a block proposal scale with the amount of included [attestations](https://kb.beaconcha.in/attestation). Theoretically, block proposers could include aggregated attestations from a parent block, but there is incentive to do so.&#x20;

Each included attestation in a block will be rewarded (if it is the first time that is included in a block) with `base_reward/8` where `8` is the `Proposer_Reward_Quotient`&#x20;

There is **no** penalty for not proposing a block.\
\
A block proposer which includes slashing will be rewarded with the `slashed_validators_effective_balance / 512` where `512` is the `Whistleblower_reward_quotient`





_Sources_ \
[_https://consensys.net/blog/codefi/rewards-and-penalties-on-ethereum-20-phase-0/_](https://consensys.net/blog/codefi/rewards-and-penalties-on-ethereum-20-phase-0/)\
[_https://benjaminion.xyz/eth2-annotated-spec/phase0/beacon-chain/_](https://benjaminion.xyz/eth2-annotated-spec/phase0/beacon-chain/)\
