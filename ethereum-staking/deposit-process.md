---
description: Ethereum staking deposit process
---

# Deposit Process

This post will explain the depositing process and each of the phases.

Before we start, to understand the basic idea of how Ethereum 2.0 keys work, the [Ethereum 2.0 Keys](https://kb.beaconcha.in/ethereum-2-keys) blog is highly recommended

## The deposit contract

![](<../.gitbook/assets/image (186).png>)

Let's go through each of the **states** above and explain how their **durations** are approximately determined.

## **1. Mempool - Status: Unknown**

Every signed transaction visits the **Mempool** first, which can be referred to as the waiting room for transactions. During this period, the _transaction status_ is [_pending_](https://etherscan.io/txsPending).\
Depending on the chosen **gas fee** for the transaction, miners pick the ones that return them the most value first. If the network is highly congested (=many pending transactions), there's a high chance that new transactions will outbid(gas fees) older transactions, leading to **unknown** waiting times.

## 2. Deposit contract - Status: Deposited

Once the transaction reaches the **deposit contract,** the deposit contract checks the transaction for its **Input data** and **value.**\
If the **threshold** of 1 ETH is not met or the transaction has **no/invalid** input data, the transaction will get **rejected** and returned to the sender.

{% hint style="info" %}
The user-created **input data** is a reflection of the upcoming **validator and withdrawal keys** on the Ethereum 2.0 network as seen in the picture below. The full Ethereum 2.0 keys blog is [here](https://kb.beaconcha.in/ethereum-2-keys).
{% endhint %}

#### **Why exactly does this take at least 13.6 hours?**

The Ethereum 2.0 chain only considers transactions which have been in the deposit contract for at least 2048 Ethereum 1.0 blocks to ensure they never end up in a [reorged](https://en.bitcoin.it/wiki/Chain\_Reorganization) block. **(=**`ETH1_FOLLOW_DISTANCE`**)**

In addition to the 2048 Ethereum 1.0 blocks, 64 **Ethereum 2.0** [**Epochs**](https://kb.beaconcha.in/glossary#epoch) \*\*\*\*must be\*\*\*\* awaited before the beacon-chain recognises the deposit. During these 64 Epochs, validators vote on newly received deposits.

However, [missed block](https://kb.beaconcha.in/glossary#block-status) proposals or bad Ethereum 1.0 nodes, which provide the deposit logs to the Ethereum 2.0 network can cause longer waiting times.\
Therefore, run your [own node](https://kb.beaconcha.in/run-a-goerli-node-eth1-and-beaconnode-eth2)!

**2048 blocks** = 2048 x 12 seconds = 24,576 seconds = 409.6 minutes = **\~6.82 hours**\
**64 Epochs** = 64 x 6.4 minutes = 409.6 minutes = **\~6.82 hours**

![](<../.gitbook/assets/image (115).png>)

Once the deposit is in the deposit contract, the state of the validator will switch to _**Deposited**_ on the [beaconcha.in](https://mainnet.beaconcha.in/validator/0xa40fa34c70f5958524a45c748b4054dda3add825fb37b7614eba1796da31ea73891a69dfddf823409230f78e7fc9b10d) explorer

{% tabs %}
{% tab title="Rejected Deposit" %}
![Rejected Transaction](<../.gitbook/assets/image (78) (1).png>)
{% endtab %}
{% endtabs %}

## 3. Validator Queue - Status: Pending

![](<../.gitbook/assets/image (17).png>)

The deposit is accessible now for the beacon-chain. Depending on the amount of total deposits, the validators have to wait in a queue. Eight validators per [Epoch](https://kb.beaconcha.in/glossary#epoch) (**1800 validators per day)** can get activated.

## 4. Staking - Status: Active

![](<../.gitbook/assets/image (70).png>)

The validator is now actively staking. It is proposing blocks and signing attestations - ready to earn ETH!

## Other validator status

#### Deposit Invalid

The transaction had an invalid [BLS](https://kb.beaconcha.in/ethereum-2-keys#general) signature.

![](<../.gitbook/assets/image (43).png>)

#### Active Offline

An active validator has not been attesting for at least two epochs.

![](<../.gitbook/assets/image (28).png>)

#### Exiting Online

The validator **is online** and currently exiting the network because either its **balance dropped below 16ETH (forced exit)** or the **exit was requested** **(voluntary exit)** by the validator.

![](<../.gitbook/assets/image (39).png>)

#### Exiting Offline

The validator **is offline** and currently exiting the network because either its **balance dropped below 16ETH** or the **exit was requested** by the validator.

![](<../.gitbook/assets/image (33).png>)

#### Slashing Online

The validator **is online** but was malicious and therefore forced to **exit** the network.

![](<../.gitbook/assets/image (55).png>)

#### Slashing Offline

The validator **is offline** and was malicious and which lead to a forced to exit out of the network.\
The validator is currently in the exiting queue with a minimum of 25 minutes.

![](<../.gitbook/assets/image (56).png>)

#### Slashed

The validator has been kicked out of the network. The funds will be withdrawable after 36 days.

![](<../.gitbook/assets/image (53).png>)

#### Exited

The validator has exited the network. The funds will be withdrawable after 1 day.

![](<../.gitbook/assets/image (20).png>)
