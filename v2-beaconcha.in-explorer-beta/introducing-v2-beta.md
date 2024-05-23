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

V2-beta introduces a new validator dashboard with a variety of new features and addresses issues observed in the past years when monitoring validators. We have worked tirelessly over the last year and will roll out more features over the next weeks.&#x20;

During our transition to v2, the v1 code base will not receive any updates unless there are critical issues. Expect all new features to launch in our new github repository here: _TBD_\


\
New **v2 validator dashboard features**

\
**Data**

v2 introduces real-time data for identifying problems and aggregated historical data for debugging and research purposes. Users will no longer need to \*read\* the tables to spot problems with their validators; instead, they can \*look\* at the slot viz which provides multi-color feedback, and the best part – it scales to up to 100,000 validators per dashboard.

**Groups**

Many of our users manage multiple nodes and servers, and it has been difficult to identify issues without a complex Grafana dashboard or a dedicated DevOps team. To address this, we have introduced "Groups," which allow users to assign validators to groups and track them separately in real-time.

\
**Sharing**

Sharing Grafana login information in large corporations can be complicated; the new Sharing feature allows users to easily provide view-only access to their team members.

\
**New Metric: Efficiency**

The familiar "Attestation Effectiveness" metric has been replaced by a new metric called "Efficiency," which considers all validator duties and provides better feedback to the user.

\
<mark style="color:red;">**\[video]**</mark>



