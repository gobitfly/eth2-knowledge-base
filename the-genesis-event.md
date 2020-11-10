---
description: A visualisation of the Genesis Event on Ethereum 2.0
---

# The Genesis Event

## Keywords

* [Deposit contract](https://github.com/gobitfly/eth2-beaconchain-explorer/pull/262)
* `Seconds_Per_Eth1_Block` = 14 seconds
* `Eth1_Follow_Distance =` 1024 blocks \* 14 seconds
* `Min_Genesis_Time` = a unix timestamp \(=this has yet to be decided\)
* `Min_Genesis_Active_Validator_Count` = 16,384
* `Genesis_Delay` = 7 days 
* [Ethereum 2.0 Beacon-chain](https://kb.beaconcha.in/glossary#beacon-chain)

## Genesis Event

### Conditions

There are two conditions which have to get triggered to get the Ethereum 2.0 chain started!

1. The threshold of **16,384 validators** needs to be hit
2. The  **ETH1** block \(=Trigger block\) which **determines the genesis** time for ETH2 **cannot be earlier** than  `min_genesis_time.`

_Trigger ETH1 block = `min_genesis_time - genesis_delay`_

###  Scenario One 

The required amount of deposits \(`Min_Genesis_Active_Validator_Count)` to fulfil the first condition occurs very quickly once the deposit contract has been deployed and **before** `min_genesis_time`.   
  
Once the threshold of **16,384 deposits** is met, the network will try to accomplish the second condition by trying to find the **trigger block** by calculating `min_genesis_time - genesis_delay.`

The goal of the trigger block `(min_genesis_time - genesis_delay)` is that the chain can never start earlier than `min_genesis_time`. The second scenario will make this clearer.

![](.gitbook/assets/image%20%28182%29.png)

### Scenario Two

The required amount of deposits \(`Min_Genesis_Active_Validator_Count)` to fulfil the first condition occurs **after** `min_genesis_time.`   
  
In this case, the second condition is met first and the trigger block becomes whatever `min_genesis_time` was set.   
The trigger block \(second condition\) is achieved right after the deposit contract receives 16,384 validator deposits.   
Genesis time becomes `Trigger-block-timestamp + genesis_delay`.

![](.gitbook/assets/image%20%28183%29.png)





_Sources:_   
[_Ethereum 2.0 Spec_](https://github.com/ethereum/eth2.0-specs/blob/dev/specs/phase0/beacon-chain.md#configuration)  
__[_The Genesis of a Beacon Chain_](https://hackmd.io/@benjaminion/genesis)\_\_

