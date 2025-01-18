---
description: Visualizes your validator performance in multiple time frames
---

# 🦸 Summary view

The summary table is part of the [validator dashboard](https://v2-beta-mainnet.beaconcha.in/dashboard). It provides detailed performance metrics for each validator [group](validator-groups.md), including [efficiency](summary-table.md#efficiency) and validator rewards across various time frames. It also features a [historical chart view](summary-table.md#summary-chart-view).

***

## Overview

Each row in the summary table represents a [validator group](validator-groups.md). Users with multiple groups will see an additional row above the thin orange line, labeled as the Σ-row.

<figure><img src="../.gitbook/assets/image (222).png" alt=""><figcaption></figcaption></figure>

### Expandable rows

Expanding a row provides detailed data for each group.

<figure><img src="../.gitbook/assets/image (211).png" alt=""><figcaption></figcaption></figure>

### Absolute vs relative values

The summary table can be viewed in both absolute and relative values. This feature is especially useful for large entities with millions of attestations that prefer a relative value.

<figure><img src="../.gitbook/assets/image (197).png" alt=""><figcaption></figcaption></figure>

1. **Summary table with relative values**

<figure><img src="../.gitbook/assets/image (195).png" alt=""><figcaption><p><strong>Summary table with relative values</strong></p></figcaption></figure>

2. **Summary table with absolute values**

<figure><img src="../.gitbook/assets/image (194).png" alt=""><figcaption><p><strong>Summary table with absolute values</strong></p></figcaption></figure>

## Missed rewards

The missed rewards, which include both the consensus layer and the execution layer, are determined by calculating the median (P50) of the rewards from slots where the specified criteria are met for each missed slot. This missed reward metric utilizes the MEV reward provided by relays for missed transaction rewards.&#x20;

`slot >= missed.slot - 16` AND `slot < missed.slot + 16`

### Missed Rewards Calculation

When a validator misses rewards — whether from the Consensus Layer (CL) or Execution Layer (EL) proposals, including MEV — those missed rewards are calculated using the median (p50) of the surrounding rewards. Specifically:

1. **Identify the Surrounding Slots**
   * For each missed slot, consider the 32 slots surrounding it: slots where `slot >= missed.slot - 16` AND `slot < missed.slot + 16`
2. **Calculate the Median (p50)**
   * Collect the rewards from each of those surrounding 32 slots.
   * Compute the _median_ (50th percentile, or p50) of that set of rewards.\

3. **Assign the Median as the Missed Reward**
   * The resulting median value becomes the _missed reward_ for that specific slot.

#### Example

* Suppose a missed proposal occurred at slot `100`.
  * Look at slots `84` through `115` (i.e., `100 - 16` to `100 + 15`).
  * Gather each validator’s reward (MEV rewards + CL rewards) from those slots.
  * Sort these rewards and take the median value.
  * The median is then recorded as the missed reward for slot `100`.



## APR calculation

The total rewards are divided by the number of hours in the selected period and then by the 32 ETH stake per validator to calculate the base hourly return per validator. This hourly rate is then scaled up to an annual percentage.

`APR = ((RewardsInPeriod / HoursInPeriod) / (32 * ValidatorCount)) * (24 * 365) * 100`

{% hint style="warning" %}
The **All time** period currently shows the **90-day APR**. This is subject to change in the future.
{% endhint %}

<figure><img src="../.gitbook/assets/apr.png" alt=""><figcaption></figcaption></figure>

## Luck calculation

<figure><img src="../.gitbook/assets/luck.png" alt=""><figcaption></figcaption></figure>

Validators are randomly selected for duties, such as proposing blocks or participating in the sync committee. The chance of being assigned duties depends on the total number of validators on the network and their effective balance.

{% hint style="info" %}
Luck values are purely informative and cannot be actively influenced.
{% endhint %}

**Blocks**

1. It is calculated how likely a validator was to be chosen to propose a block in each epoch.

```
ExpectedBlocks = (ValidatorEffectiveBalance / NetworkEffectiveBalance) * SlotsPerEpoch
```

2. The number of blocks a validator proposed is measured against the expected number, expressed as a percentage.

```
BlockLuckPercent = (ProposedBlocks / ExpectedBlocks) * 100
```

In practice, this calculation is performed for all validators over the selected time frame.

**Sync Committee**

1. It is calculated how likely it was for a validator to be chosen as a member of the sync committee in each election.

```
ExpectedSyncParticipations = (ValidatorEffectiveBalance / NetworkEffectiveBalance) * SyncCommitteeSize
```

2. The number of actual participations is compared to the expected participations and expressed as a percentage.

```
SyncLuckPercent = (ActualSyncParticipations / ExpectedSyncParticipations) * 100
```

In practice, this calculation is performed for all validators over the selected time frame.

## Summary chart view

`[1]` View the historical performance of your validator groups by clicking this button and switching to the summary chart view.\\

<figure><img src="../.gitbook/assets/image (212).png" alt=""><figcaption></figcaption></figure>

`[2]` The summary chart view is perfect for debugging issues, as it provides historical performance data with epoch-level granularity. The Groups dropdown lets users filter specific groups, while the Total line (orange line) shows the average performance of all groups in the dashboard.\
\
To identify missed blocks, sync duties, or attestations, users can use the Efficiency dropdown to filter for those specific duties.

<figure><img src="../.gitbook/assets/image (213).png" alt=""><figcaption></figcaption></figure>

## Status column

The status column offers a quick way to check key duties, such as your current sync committees, whether you're part of the upcoming sync committee, and if any of your validators have been slashed.\
\
Hover over the icons for more details.

<figure><img src="../.gitbook/assets/image (223).png" alt=""><figcaption></figcaption></figure>

## Validator column

The validator column displays the state of each validator in each group:

* Online validators (green icon)
* Offline validators (red icon)
* Exited validators (gray icon)

A comma-separated list of validator indices for each group can be found in the popout modal for each row in the table.

<figure><img src="../.gitbook/assets/image (206).png" alt=""><figcaption><p>Validator states</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (224).png" alt=""><figcaption><p>Validators state in relative values</p></figcaption></figure>

_The relative value only accounts for online and offline validators, ignoring those that have already exited the chain. This offers quick insights into whether your group is experiencing issues._

<figure><img src="../.gitbook/assets/image (210).png" alt="" width="227"><figcaption><p>Popout modal with comma separated validator indices</p></figcaption></figure>

## Efficiency

The Validator [Efficiency](summary-table.md#efficiency) metric is a new, comprehensive measure of validator performance, combining multiple components:

* **Red arrow**: Underperforming the network average by at least 0.25%.
* **Green arrow**: Outperforming the network average by at least 0.25%.
* **Yellow arrow**: Within a range of +/- 0.25% of the network average.

Hovering over an arrow displays the exact performance of each group. For historical performance, switch to the summary chart view.

<figure><img src="../.gitbook/assets/image (218).png" alt=""><figcaption></figcaption></figure>

### Attestations vs Attester efficiency

* **Attester Efficiency**: This measures how much reward a validator could have earned for attestations versus how much they actually earned. For example, if a validator could have earned 100 GWEI for attestations but only received 98 GWEI, the attester efficiency would be 98%.
* **Attestations (%-value)**: This represents the percentage of attestations successfully included in the network. For instance, if a validator managed to include 99 out of 100 attestations, the Attestation (%) value would be 99%.

The absolute values can be viewed by hovering over this percentage or by switching to the absolute-table view.

<figure><img src="../.gitbook/assets/image (198).png" alt=""><figcaption></figcaption></figure>
