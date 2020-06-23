# Ethereum 2.0 & Depositing Process

Due to confusion on how depositing works, especially without the usage of prylabs.net/participate, this post will guide you through the process and explain relevant steps!  
  
Before we start off, in order to understand the basic idea of how Ethereum 2.0 keys work, the [Ethereum 2.0 Keys](https://kb.beaconcha.in/ethereum-2-keys) blog is highly recommended.

## The deposit contract

![](.gitbook/assets/image%20%2883%29.png)

  
Let's go through each of the **Status** above and explain how their **durations** are approximately determined.  
In order to interact with the deposit contract, the transaction requires a **gas limit of ~500,000** an a minimum of 1 ETH. Top ups are [possible](https://kb.beaconcha.in/ethereum-2-keys#what-happens-to-multiple-deposits-from-a-single-eth1-wallet-multiple-validators)!

####  **1. Mempool - Time: Unknown**

Every signed transaction visits the **Mempool** first, which can be referred to as the waiting room for transactions. During this period, the _transaction status_ is usually [_pending_](https://etherscan.io/txsPending).   
Depending on the chosen **gas fee** for the transaction, miners pick the ones that return them the most value first. If the network is highly congested \(=many pending transactions\), there's a high chance that your gas fees will be outbid, leading to **unknown** waiting times.



#### 2. Deposit contract - Time: Unknown

Once the transaction reaches the **deposit contract,** the contract checks the transaction for its **Input data** and **the transaction value \(=amount of ETH\).**   
If the **threshold** of 1 ETH is not met or the transaction has **no/invalid** input data, the transaction gets **rejected** and returned to the sender.  
  
The user-created **input data**, is a reflection of the upcoming **validator and withdrawal keys** on the Ethereum 2.0 network as seen below. Our full Ethereum 2.0 keys blog is [here](https://kb.beaconcha.in/ethereum-2-keys).

{% tabs %}
{% tab title="Input Data \(ETH 2.0 Keys\)" %}
![ETH 2.0 Key Generation via Input Data](.gitbook/assets/image%20%2875%29.png)
{% endtab %}

{% tab title="Rejected Transaction" %}
![Rejected Transaction](.gitbook/assets/image%20%2877%29.png)
{% endtab %}
{% endtabs %}





![](.gitbook/assets/image%20%2879%29.png)





