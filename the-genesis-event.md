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

There are two conditions that have to be met to trigger the Ethereum 2.0 chain

1. The threshold of **16,384 validators** has been hit
2. The  **ETH1** block \(=Trigger block\) which **determines the genesis** time for ETH2 **cannot be earlier** than  `min_genesis_time - genesis_delay (7d)`

###  Scenario One

`min_genesis_time - genesis_delay <= min_genesis_time`

Once the threshold of **16,384 deposits** has been met, the network will try to accomplish the second condition. Now the system tries to find the **trigger block** by calculating `min_genesis_time - genesis_delay.`

![](.gitbook/assets/image%20%28174%29.png)

### Scenario Two

![](.gitbook/assets/image%20%28172%29.png)





_Sources:_   
[_Ethereum 2.0 Spec_](https://github.com/ethereum/eth2.0-specs/blob/dev/specs/phase0/beacon-chain.md#configuration)  
__[_The Genesis of a Beacon Chain_](https://hackmd.io/@benjaminion/genesis)\_\_

