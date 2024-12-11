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

## APR and Luck calculation

<mark style="color:red;">**WIP**</mark>

## Summary chart view

`[1]` View the historical performance of your validator groups by clicking this button and switching to the summary chart view.\


<figure><img src="../.gitbook/assets/image (212).png" alt=""><figcaption></figcaption></figure>

`[2]` The summary chart view is perfect for debugging issues, as it provides historical performance data with epoch-level granularity. The Groups dropdown lets users filter specific groups, while the Total line (orange line) shows the average performance of all groups in the dashboard. \
\
To identify missed blocks, sync duties, or attestations, users can use the Efficiency dropdown to filter for those specific duties.

<figure><img src="../.gitbook/assets/image (213).png" alt=""><figcaption></figcaption></figure>

## Status column

The status column offers a quick way to check key duties, such as your current sync committees, whether you're part of the upcoming sync committee, and if any of your validators have been slashed. \
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



<figure><img src="../.gitbook/assets/image (210).png" alt="" width="227"><figcaption><p>Popout modal with comma separated  validator indices</p></figcaption></figure>





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











