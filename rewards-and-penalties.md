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

**Head, Source, target,** can be either positive or negative, however the **inclusion delay** can just be positive. The **Source** has to be **correct** in order to get included. 

![](.gitbook/assets/grafik%20%2811%29.png)

![](.gitbook/assets/image%20%28193%29.png)

**Possible Attestation properties**

![](.gitbook/assets/image%20%28194%29.png)

The **worst** inclusion speed reward is **base\_reward\*1/28** with an inclusion distance of 32 ****and the **best** is **base\_reward\*7/8** with an inclusion distance of 1.

**Best possible reward**  
3 \* base reward + base reward \* \(base reward \* 7/8\)  
  
**Worst possible reward with an included attestation \("Negative Reward"\)**  
\(base reward\) - \( 2 \* base reward \) + \(base reward \* 1/28\)



{% hint style="info" %}
THIS POST IS WORK IN PROGRESS AND VERY LIKELY TO BE WRONG
{% endhint %}



### Block reward 

