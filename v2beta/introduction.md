---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 🎉 Introducing v2-beta

V2-beta introduces a new validator dashboard with a variety of new features and addresses issues observed in the past years when monitoring validators. Most importantly, it scales up to 100,000 validators, a 35,600% increase over our V1 dashboard.\
\
We have worked tirelessly over the last year and will roll out more features over the next weeks.&#x20;

During our transition to v2, the v1 code base will not receive any updates unless there are critical issues. Expect all new features to launch in our new github repository here: [https://github.com/gobitfly/beaconchain](https://github.com/gobitfly/beaconchain)

Mainnet:  [https://v2-beta-mainnet.beaconcha.in/dashboard](https://v2-beta-mainnet.beaconcha.in/dashboard)

Holesky:  [https://v2-beta-holesky.beaconcha.in/dashboard](https://v2-beta-holesky.beaconcha.in/dashboard)

***

**New v2 validator dashboard features**

\
[**Data**](summary-table.md)

v2 introduces real-time data for identifying problems and aggregated historical data for debugging and research purposes. Users will no longer need to _read_ the tables to spot problems with their validators; instead, they can _look_ at the slot viz which provides [multi-color feedback](slot-visualization.md), and the best part – it scales to up to 100,000 validators per dashboard.

[**Groups**](validator-groups.md)

Many of our users manage multiple nodes and servers, and it has been difficult to identify issues without a complex Grafana dashboard or a dedicated DevOps team. To address this, we have introduced "Groups," which allow users to assign validators to groups and track them separately in real-time.

\
[**Sharing**](share-your-custom-dashboard.md)

Sharing Grafana login information in large corporations can be complicated; the new Sharing feature allows users to easily provide view-only access to their team members.

\
**New Metric:** [**Efficiency**](metric-validator-efficiency.md)

The familiar "Attestation Effectiveness" metric has been replaced by a new metric called "Efficiency," which considers all validator duties and provides better feedback to the user.



{% hint style="success" %}
For those who have been subscribed to beaconcha.in in the past -- Thank you for supporting us!

<mark style="color:green;">You will have access to the new premium features for the same price.</mark>\


* Plankton and Goldfish subscribers have been migrated to '[Guppy](https://v2-beta-holesky.beaconcha.in/pricing).'&#x20;
* Whale subscribers have been migrated to '[Dolphin](https://v2-beta-holesky.beaconcha.in/pricing)'.
{% endhint %}
