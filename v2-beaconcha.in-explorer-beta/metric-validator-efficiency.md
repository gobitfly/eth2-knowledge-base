---
description: Efficiency, a metric to measure validator performance
---

# 📈 Metric: Validator Efficiency

The validator **Efficiency** metric is a comprehensive measure of validator performance, integrating multiple components:&#x20;

1. [**Attestations**](metric-validator-efficiency.md#attester-efficiency)
2. **Block proposals**
3. **Sync committees**.&#x20;

This metric is designed to provide a holistic view of a validator's effectiveness. \
\
Some examples are available here.

***

**Components of Efficiency**\



{% hint style="info" %}
Note that the duty weighting is based on the consensus layer specification.&#x20;

Huge thanks to [Ben Edington](https://x.com/benjaminion\_xyz) for providing [https://eth2book.info/capella/](https://eth2book.info/capella/)
{% endhint %}

### **Attester Efficiency** 

84.4% (= 54/64)  of validators' rewards come from attestations. Every epoch (\~6.4 minutes), a validator proposes an attestation (vote) to the network.&#x20;

These attestations contain valuable information about the consensus layer and are rewarded based on their correctness and inclusion delay.

An attestation consists of three votes:

\- Head vote

\- Source vote

\- Target vote

If a validator votes correctly on all three and is included in the block with the best inclusion delay (1), the reward will be 100%, as good as it can be.

Conveniently, the [beacon node API](https://ethereum.github.io/beacon-APIs/#/Rewards/getAttestationsRewards) returns the idealReward for a given epoch. The idealReward represents the maximum potential rewards based on optimal performance, which allows us to calculate attester efficiency.

{% code overflow="wrap" %}
```
attester_efficiency = actualReward / idealReward
```
{% endcode %}



***

### Proposer Efficiency

Block proposals are purely luck-based, but over the long run, 12.5% (8/64) of validators' rewards come from block proposals. Blocks include execution rewards (transaction rewards + MEV rewards) and scale with the number of attestations and sync committee outputs included in a block.

Comparing validator performance based on the luck of inclusion of attestations and MEV rewards (which highly depend on market volatility) would not provide meaningful context. Thus, proposer efficiency solely depends on the number of successfully proposed blocks divided by the total number of blocks that a validator could have proposed.

\
This leads to the following formula:

{% code overflow="wrap" %}
```
proposer_efficiency = proposedBlocks / totalBlocks
```
{% endcode %}

Some validators may not be lucky enough to propose a block, but their efficiency needs to be comparable with other validators who did propose a block. For this reason, the proposer efficiency will be `1` for validators who did not propose a block. Our v2 dashboard and API will provide both proposal efficiency and efficiency to provide more context.

***

### Sync Efficiency

Every 256 epochs, 512 validators are elected to be part of the sync committee. Like block proposals, being part of a sync committee is purely luck-based. However, over the long run, 3.1% (2/64) of validators' rewards come from sync committee duties. With 500,000 validators, the expected time between being selected for sync committee duty is approximately 37 months. During this period, the rewards for sync committee members are significantly higher.

Compared to attestations, which occur once per epoch, sync duties occur in every slot for 256 epochs, totaling 8192 duties per sync committee member.

To reflect actual performance, sync efficiency doesn’t rely on rewards but on the number of correctly executed sync duties. To avoid skewing the sync efficiency by the scheduled duties, we divide it. Since sync duties need to be included in a block by the block proposer, we subtract missed blocks that occurred during this period to avoid penalizing the sync committee member.



This leads to the following formula

{% code overflow="wrap" %}
```html
sync_efficiency = executed_Sync / (scheduled_Sync - missed_Blocks)
```
{% endcode %}

Validators may not be lucky enough to be elected in a sync committee, but their efficiency needs to be comparable with other validators who did participate. For this reason, the sync efficiency will be `1` for validators who were not elected. Our v2 dashboard and API will provide both proposal efficiency and efficiency to provide more context.



***

### Examples: Efficiency calculation



Example 1

When a validator has **attestations, block proposals, and sync committees**, the efficiency is calculated as:

{% code overflow="wrap" %}
```
efficiency = ((54/64 * attester_efficiency) + (8/64 * proposer_efficiency) + (2/64 * sync_efficiency))
```
{% endcode %}



Example 2\
\
For validators who have participated in attestations and block proposals **but not in sync committees**, the efficiency is computed as:

{% code overflow="wrap" %}
```
efficiency = ((56/64 * attester_efficiency) + (8/64 * proposer_efficiency))
```
{% endcode %}



Example 3\
\
When a validator has participated in attestations and sync committees **but not in block proposals**, the efficiency formula is:

{% code overflow="wrap" %}
```
efficiency = ((62/64 * attester_efficiency) + (2/64 * sync_efficiency))
```
{% endcode %}



Example 4

If a validator has participated only in attestations, the efficiency is simply:

```
efficiency = 1 * attester_efficiency
```





