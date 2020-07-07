# Ethereum 2.0 - Depositing Process

This post will explain the depositing process and each of the phases.  
  
Before we start, to understand the basic idea of how Ethereum 2.0 keys work, the [Ethereum 2.0 Keys](https://kb.beaconcha.in/ethereum-2-keys) blog is highly recommended.

## The deposit contract

![](../.gitbook/assets/image%20%28120%29.png)

Let's go through each of the **states** above and explain how their **durations** are approximately determined.

## **1. Mempool - Status: Unknown**

Every signed transaction visits the **Mempool** first, which can be referred to as the waiting room for transactions. During this period, the _transaction status_ is [_pending_](https://etherscan.io/txsPending).   
Depending on the chosen **gas fee** for the transaction, miners pick the ones that return them the most value first. If the network is highly congested \(=many pending transactions\), there's a high chance that new transactions will outbid\(gas fees\) older transactions, leading to **unknown** waiting times.

## 2. Deposit contract - Status: Deposited

Once the transaction reaches the **deposit contract,** the deposit contract checks the transaction for its **Input data** and **value.**   
If the **threshold** of 1 ETH is not met or the transaction has **no/invalid** input data, the transaction gets **rejected** and returned to the sender.

{% hint style="info" %}
The user-created **input data** is a reflection of the upcoming **validator and withdrawal keys** on the Ethereum 2.0 network as seen in the picture below. The full Ethereum 2.0 keys blog is [here](https://kb.beaconcha.in/ethereum-2-keys).
{% endhint %}

#### **Why exactly does this take 7.5 hours?**

The Ethereum 2.0 chain only considers transactions which have been in the deposit contract for 1024  Ethereum 1.0 blocks to ensure they never end up in a [reorged](https://en.bitcoin.it/wiki/Chain_Reorganization) block.   
**\(=**`ETH1_FOLLOW_DISTANCE` referred by [developers](https://benjaminion.xyz/eth2-annotated-spec/phase0/beacon-chain/configuration/#misc).\)   
  
****In addition to the 1024 Ethereum 1.0 blocks, 32 **Ethereum 2.0** [**Epochs**](https://kb.beaconcha.in/glossary#epoch) ****must be ****awaited before the beacon-chain recognises the deposit. During these 32 Epochs, validators vote on newly received deposits.   
  
However, [missed block](https://kb.beaconcha.in/glossary#block-status) proposals or bad Ethereum 1.0 nodes, which provide the deposit logs to the Ethereum 2.0 network can cause longer waiting times.   
Therefore, run your [own node](https://kb.beaconcha.in/run-a-goerli-node-eth1-and-beaconnode-eth2)!  
  
**1024 blocks** = 1024 x **~**13 seconds = 13,312 seconds = **~4 hours**  
**32 Epochs** = 32 x 6.4 minutes =  204.8 minutes = **~3.5 hours**

![](../.gitbook/assets/image%20%28115%29.png)

Also, when the Ethereum 2.0 chain recognizes the deposit \(after 7.5 hours\), the validator status will change to _**Deposited**_ on the [beaconcha.in](https://beaconcha.in/validator/0) explorer.

{% tabs %}
{% tab title="Rejected Deposit" %}
![Rejected Transaction](../.gitbook/assets/image%20%2878%29.png)
{% endtab %}
{% endtabs %}



## 3. Validator Queue - Status: Pending

![](../.gitbook/assets/image%20%28108%29.png)

The deposit is accessible now for the beacon-chain. Depending on how many deposits have occurred, there is a queue. Only four validators per [Epoch](https://kb.beaconcha.in/glossary#epoch) \(**900 validators per day\)** get activated.  
  
**Note:**   
The first 16,384 Validators, the genesis validators, do **not** line up in a queue, but instantly start staking from [Slot](https://kb.beaconcha.in/glossary#slots-32-slots-1-epoch) 0.

## 4. Staking - Status: Active

![](../.gitbook/assets/image%20%28112%29.png)

The validator is now actively staking, proposing blocks and signing attestations - ready to earn rewards!

## Other validator status



#### Deposit Invalid

The transaction had an invalid [BLS](https://kb.beaconcha.in/ethereum-2-keys#general) signature.

![](../.gitbook/assets/image%20%28110%29.png)

#### Active Offline

An active validator has not been attesting for two epochs.

![](../.gitbook/assets/image%20%28117%29.png)

#### Exiting Online

The validator **is online** and currently exiting the network because either its **balance dropped below 16ETH** or the **exit was requested** by the validator.

![](../.gitbook/assets/image%20%28104%29.png)

#### Exiting Offline 

The validator **is offline** and currently exiting the network because either its **balance dropped below 16ETH** or the **exit was requested** by the validator.

![](../.gitbook/assets/image%20%28103%29.png)

#### Slashing Online

The validator **is online** but has been malicious and was forced to exit the network.

![](../.gitbook/assets/image%20%28105%29.png)

#### Slashing Offline 

The validator **is offline** but has been malicious and was forced to exit the network.   
It is currently in the exiting queue with a minimum of 25 minutes.

![](../.gitbook/assets/image%20%28114%29.png)

#### Slashed

The validator has been kicked out of the network. The funds will be withdrawable after 36 days.

![](../.gitbook/assets/image%20%28106%29.png)

#### Exited

The validator has exited the network. The funds will be withdrawable after 1 day.

![](../.gitbook/assets/image%20%28116%29.png)



