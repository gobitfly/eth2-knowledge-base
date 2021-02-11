---
description: The journey of a validator balance
---

# Rewards and Penalties

A simplified overview of the most common validator rewards. 

## Epoch

A validator can propose **one attestation** and **one block** per epoch and depending on their properties the reward varies.

### Attestation reward

Rewards and penalties are based on the correctness of

* **Source:** base\_reward
* **Head:** base\_reward
* **Target:** base\_reward

![](.gitbook/assets/grafik%20%2811%29.png)

![](.gitbook/assets/grafik%20%2816%29.png)

**Head, Source, target,** can be either positive or negative, however the **inclusion delay** can just be positive. The **Source** has to be **correct** in order to get included. 

The lowest attestation inclusion delay reward is **base\_fee\*1/28** and the maximum is **base\_fee\*8/7**

![](.gitbook/assets/grafik%20%2813%29.png)

{% hint style="info" %}
THIS POST IS WORK IN PROGRESS AND VERY LIKELY TO BE WRONG
{% endhint %}



### Block reward 

