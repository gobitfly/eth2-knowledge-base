---
description: Efficiency, a metric to measure validator performance
---

# 📈 Metric: Validator Efficiency

The validator **Efficiency** metric is a comprehensive measure of validator performance, integrating multiple components:&#x20;

1. [**Attestations**](metric-validator-efficiency.md#attester-efficiency)
2. [**Block proposals**](metric-validator-efficiency.md#proposer-efficiency)
3. [**Sync committees**](metric-validator-efficiency.md#sync-efficiency)

This metric is designed to provide a holistic view of a validator's effectiveness. \
\

Validator efficiency can be calculated over an arbitrary timeframe. The longer the timeframe, the closer it is expected to approach the duty weighting as defined in the consensus layer specification. For shorter timeframes however (down to a single epoch), these values can vary significantly: A block proposal or sync committee participation can completely dominate the resulting efficiency in these cases.&#x20;

In order to calculate the efficiency over multiple epochs correctly, the respective effective balance has to be factored in. To accomplish this, each individual value gets aggregated before calculating the percentage efficiency, instead of calculating the percentage for each epoch and averaging that.

***

**Components of Efficiency**\



{% hint style="info" %}
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

Conveniently, the [beacon node API](https://ethereum.github.io/beacon-APIs/#/Rewards/getAttestationsRewards) returns the idealReward for a given epoch. The idealReward represents the maximum potential rewards based on optimal performance, which allows us to calculate attester efficiency. Negative rewards (penalties) from any of the 3 attestation components do not count towards `attester_actualReward`.

{% code overflow="wrap" %}
```
attester_efficiency = attester_actualReward / attester_idealReward
```
{% endcode %}



***

### Proposer Efficiency

Block proposals are purely luck-based, but over the long run, 12.5% (8/64) of validators' rewards come from block proposals. Blocks include execution rewards (transaction rewards + MEV rewards) and scale with the number of attestations and sync committee outputs included in a block.

Comparing validator performance based on MEV rewards (which highly depend on market volatility) would not provide meaningful context. Thus, proposer efficiency solely depends on CL rewards. To remove some volatility from the result, the received proposal-related rewards are compared to the median proposal-related reward of surrounding proposals. Specifically, the surrounding 32 proposals (missing skipped, 0 if none) of each proposal are considered to be the the median proposal reward.
\
This leads to the following formula:

{% code overflow="wrap" %}
```
proposer_idealReward = max(proposer_actualReward, medianReward([x-16 ... x+16]))
proposer_efficiency = proposer_actualReward / proposer_idealReward
```
{% endcode %}


***

### Sync Efficiency

Every 256 epochs, 512 validators are elected to be part of the sync committee. Like block proposals, being part of a sync committee is purely luck-based. However, over the long run, 3.1% (2/64) of validators' rewards come from sync committee duties. With 500,000 validators, the expected time between being selected for sync committee duty is approximately 37 months. During this period, the rewards for sync committee members are significantly higher.

Compared to attestations, which occur once per epoch, sync duties occur in every slot for 256 epochs, totaling 8192 duties per sync committee member.

Since sync duties need to be included in a block by the block proposer, we ignore missed blocks that occurred during this period to avoid penalizing the sync committee member. Penalties from missed sync participation are also not counted towards `sync_actualReward`.



This leads to the following formula

{% code overflow="wrap" %}
```html
sync_efficiency = sync_actualReward / sync_idealReward
```
{% endcode %}


***

### Example Efficiency calculation


When a validator has **attestations, block proposals, and sync committees**, the efficiency is calculated as:

{% code overflow="wrap" %}
```
efficiency = (attester_actualReward + proposer_actualReward + sync_actualReward) / (attester_idealReward + proposer_idealReward + sync_idealReward)
```
{% endcode %}

When a validator did not participate in a sync committee and/or did not propose a block, the respective rewards & ideal rewards are set to 0
