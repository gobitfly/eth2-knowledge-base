---
description: The journey of a validator balance
---

# Rewards and Penalties

A simplified overview of the most common validator rewards. 

## Epoch

A validator can propose **one attestation** and **one block** per epoch and depending on their properties the reward varies.

## Attestation reward

Rewards and penalties are based on the correctness of

* **Source**
* **Head**
* **Target**

**Head, Source, target,** can be either positive or negative, however the **inclusion delay** can just be positive. The **Source** has to be **correct** in order to get included. 

### Base Reward

![](.gitbook/assets/grafik%20%2811%29.png)

![](.gitbook/assets/image%20%28195%29.png)

The **worst** inclusion speed reward is **base\_reward \* 1/32 \* 7/8** with an inclusion distance of 32 ****and the **best** is **base\_reward \* 1/1 \* 7/8** with an inclusion distance of 1.

###  **Possible Attestation properties**

![](.gitbook/assets/image%20%28207%29.png)



### **Common case scenarios**

_Assumption: The participation rate is 100%_

1. You vote correctly and gets included in the next slot: you get **31/8\*base\_reward**
2. You miss head because you got a late block and it gets included in the next slot: **15/8\*base\_reward**
3. You miss head and target cause you got late a block, you get **-1/8\* base\_reward**
4. You attest and vote correctly, but the next block is missed, you get **55/16 \* base\_reward**
5. You attest correctly and get perfect inclusion distance, but you attested on a block that most people got late as in 2., you get **~7/8 \* base\_reward**  _The last one is the most confusing one: When there is a late block where validators miss the head, the validator that misses the head earns **more** than the validator that votes correctly, as in 2.  15/8 &gt; 7/8_

**Best possible reward**  
31/8 \* base\_reward  
  
**Worst possible reward with an included attestation \("Negative Reward"\)**  
-249/256 \* base\_reward

## Block reward

Only **valid** attestations \(correct source\) can be included in a block and the rewards for a block proposal scale with the amount of included [aggregated attestations](https://kb.beaconcha.in/attestation#aggregated-attestation). Theoretically, block proposers could include aggregated attestations from a parent block, but there is incentive to do so. 

Each included attestation in a block will be rewarded with `base_reward/8` where `8` is the `Proposer_Reward_Quotient` 

There is **no** penalty for not proposing a block.  
  
A block proposer which includes slashing will be rewarded with the `base_reward/8 * slashed_validators_effective_balance) / 512`

