# Ethereum 2.0 & Depositing Process

Due to confusion on how depositing works, especially without the usage of prylabs.net/participate, this post will guide you through the process and explain relevant steps!  
  
Before we start off, in order to understand the basic idea of how Ethereum 2.0 keys work, the [Ethereum 2.0 Keys](https://kb.beaconcha.in/ethereum-2-keys) blog is highly recommended.

## The deposit contract

![Depositing process](.gitbook/assets/image%20%2874%29.png)

  
Let's go through each of the **Status** above and explain how their **durations** are approximately determined.  
In order to interact with the deposit contract, the transaction requires a **gas limit of ~500,000** an a minimum of 1 ETH. Top ups are [possible](https://kb.beaconcha.in/ethereum-2-keys#what-happens-to-multiple-deposits-from-a-single-eth1-wallet-multiple-validators)!

###  **1. Mempool - Status: Unknown**

Every signed transaction visits the **Mempool** first, which can be referred to as the waiting room for transactions. During this period, the _transaction status_ is usually [_pending_](https://etherscan.io/txsPending).   
Depending on the chosen **gas fee** for the transaction, miners pick the ones that return them the most value first. If the network is highly congested \(=many pending transactions\), there's a high chance that your gas fees will be outbid, leading to **unknown** waiting times.

### 2. Deposit contract - Status: Deposited

Once the transaction reaches the **deposit contract,** the contract checks the transaction for its **Input data** and **the transaction value \(=amount of ETH\).**   
If the **threshold** of 1 ETH is not met or the transaction has **no/invalid** input data, the transaction gets **rejected** and returned to the sender.

{% hint style="info" %}
The user-created **input data**, is a reflection of the upcoming **validator and withdrawal keys** on the Ethereum 2.0 network as seen below. Our full Ethereum 2.0 keys blog is [here](https://kb.beaconcha.in/ethereum-2-keys).
{% endhint %}

#### **Why exactly does this take 7.5 hours though?**

The Ethereum 2.0 chain only considers transactions which have been in the deposit contract for 1024  Ethereum 1.0 blocks to ensure they never end up in a [reorged](https://en.bitcoin.it/wiki/Chain_Reorganization) block.   
**\(=**`ETH1_FOLLOW_DISTANCE` referred by [developers](https://benjaminion.xyz/eth2-annotated-spec/phase0/beacon-chain/configuration/#misc).\)   
  
****In addition to the 1024 Ethereum 1.0 blocks, 32 **Ethereum 2.0** [**Epochs**](https://kb.beaconcha.in/glossary#epoch) ****must be ****awaited before the beacon-chain recognises the deposit. During these 32 Epochs, validators vote on newly received deposits.   
  
However, [missed block](https://kb.beaconcha.in/glossary#block-status) proposals or bad Ethereum 1.0 nodes, which provide the deposit logs to the Ethereum 2.0 network , can cause longer waiting times.   
Therefore, run your [own nodes](https://kb.beaconcha.in/run-a-goerli-node-eth1-and-beaconnode-eth2)!  
  
1024 blocks = 1024 x **~**13 seconds = 13,312 seconds = **~4 hours**  
32 Epochs = 32 x 6.4 minutes =  204.8 minutes = **~3.5 hours**  


{% tabs %}
{% tab title="Input Data \(ETH 2.0 Keys\)" %}
![ETH 2.0 Key Generation via Input Data](.gitbook/assets/image%20%2876%29.png)
{% endtab %}

{% tab title="Rejected Transaction" %}
![Rejected Transaction](.gitbook/assets/image%20%2878%29.png)
{% endtab %}
{% endtabs %}



### 3. Validator Queue - Status: Pending



![](.gitbook/assets/image%20%2880%29.png)





