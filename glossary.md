# Glossary

## Beacon-chain

It introduces Proof of stake to Ethereum1 and runs along it. It’s also called the coordination layer.

**Roles**:

* Assign validators their duties
* Finalize checkpoints
* Perform a protocol level random number generation \(RNG\)
* Progress the beacon chain
* Vote on the head of the chain for the fork choice
* Finalize checkpoints
* Link and vote in transitions/data of shard chains

[_Run a validator & beacon-node_](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client)

[source](https://notes.ethereum.org/@djrtwo/Bkn3zpwxB#High-level-overview)

## Slots

**32 Slots = 1 Epoch**  
A time period of **12 seconds** in which a randomly chosen validator has time to propose a block. Each slot may or may not have a block in it. The total number of validators is split up in committees and one or more individual committees are responsible to attest to each slot. One validator from the committee will be chosen to propose a block, while the other 127 are attesting. After each Epoch, the validators are mixed and merged to new committees \(minimum of 128 validators per committee\).

![](https://user-images.githubusercontent.com/26490734/73458538-bd09eb80-4375-11ea-83a1-27b5fb1394a1.png)

[image source](https://medium.com/coinmonks/eth2-0-phase-0-basics-for-new-contributors-8a0a22bc38c7)

## Epoch

**1 Epoch = 32 Slots**  
Represents the number of 32 slots and takes approximately **6.4 minutes.**   
Epochs play an important role when it comes to the [validator queue](https://kb.beaconcha.in/glossary#2-pending) and [finality](https://kb.beaconcha.in/glossary#finalization). 

## Deposit contract

The Deposit contract is the **gateway** to Ethereum 2.0 **through a smart contract** on Ethereum 1.0.   
The smart contract accepts any transaction with a minimum amount of 1 ETH and a valid input data.  
Ethereum 2.0 beacon-nodes listen to the deposit contract and use the input data to credit each validator.  
   
[_More infos the Deposit Contract_](https://kb.beaconcha.in/ethereum-2.0-and-depositing-process)

## Input Data

The Input data, also called the **deposit data**, is a user generated, 842 long sequence of characters.   
It represents the [validator public key and the withdrawal public key](https://kb.beaconcha.in/ethereum-2-keys), which were signed with by the validator private key. The input data needs to be added to the transaction to the [deposit contract](https://kb.beaconcha.in/glossary#deposit-contract) in order to get identified by the [beacon-chain](https://kb.beaconcha.in/glossary#beacon-chain).  
  
[_More infos about the Deposit process._](https://kb.beaconcha.in/ethereum-2.0-and-depositing-process/depositing-to-ethereum-2.0)

## Validator

Validators need to deposit 32 ETH into the validator deposit contract on the Ethereum 1.0 chain.  
Validator operators have to run a validator node. Its job is to propose blocks and sign attestations.  
A validator has to be online for at least 50% of the time in order to have positive returns.     
  
[_Run a validator & beacon-node_](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client)\_\_

### Eligible for activation & Estimated activation

Refers to pending validators. The deposit has been recognized by the ETH2 chain at the timestamp of “Eligible for activation”. If there is a queue of [pending validators](https://www.beaconcha.in/validators), an estimated timestamp for activation is calculated.

### Unique Index

Every validator receives its unique index.  [beaconcha.in](https://www.beaconcha.in/).

![](https://user-images.githubusercontent.com/26490734/73483294-7630eb80-439f-11ea-85ef-2ce08c7a7e1a.png)

### 

### Current Balance & Effective Balance

The current balance is the amount of ETH held by the validator as of now. The **effective Balance** represents a value calculated by the current balance. It is used to determine the size of a reward or penalty a validator receives. The effective balance can **never be higher than 32 ETH.  
  
In order to increase the effective balance, the validator requires “effective balance + 1.25 ETH”.** In other words, if the effective balance is 20 ETH, a current balance of 21.25 ETH is required in order to have an effective balance of 21 ETH. The effective balance **will adjust once it drops by 0.25** below the threshold as seen in the examples above.

Here are examples on how the effective balance changes

* If the Current balance is 32.00 ETH – the Effective balance is 32.00 ETH
* If the Current balance dropped from 22 ETH to 21.76 ETH – Effective balance will be **22.00 ETH**
* If the Current balance increases to 22.25 **and** the effective balance is 21 ETH, the effective balance will increase to 22 ETH

## Slasher 

The [**slasher**](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/slasher-windows-macos--prysm) **is its own entity** but requires a beacon-node to receive [attestations](https://kb.beaconcha.in/glossary#attestation).  
To find malicious activity by validators, the slashers iterates through all received attestations until a **slashable offense** has been found.   
Found slashings are broadcasted to the network and the next [block proposer](https://kb.beaconcha.in/glossary#block-proposer) adds the proof to the block. The block proposer receives a reward for slashing the malicious validator.   
However, the whistleblower \(=Slasher\) does not receive a reward.  
  
[_More infos and how to run a slasher_](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/slasher-windows-macos--prysm)_._  
  
**Slashable offenses**

**Attestation violation**

* **Double voting**  An **attester** signs two different attestations **in one epoch.** 
* **Surround votes** An **attester** and sign an attestation that surrounds another one.

#### Proposer violation

* **Double block proposal** A **block** **proposer** signs two different blocks for the same slot.

## Attestation

Votes by validators which confirm the validity of a block. \(=Attester\)

## Block proposer

A chosen validator by the beacon chain to propose the next block. There can only be one valid block per slot.

## Block status

* **Proposed** The block passed and was proposed by a validator.
* **Scheduled**  Validators are currently submitting data.
* **Missed/Skipped**  The proposer didn’t propose the block within the given time frame, so the block was missed/skipped.
* **Orphaned**  In order to understand this, let us look at the diagram below "1, 2, 3, ... ,9" represent the slots.

1. Validator at slot 1 proposes the block “a”.
2. Validator at slot 2 proposes “b”.
3. Slot 4 is being skipped because the validator didn’t propose a block \(e.g.: offline\).
4. At slot 5/6 a fork occurs: Validator\(5\) proposes a block, but validator\(6\) doesn’t receive this data \(e.g.: the block didn’t reach them fast enough\). Therefore Validator\(6\) proposes its block with the most recent information it sees from validator\(3\).
5. The [fork choice rule](https://notes.ethereum.org/@vbuterin/rkhCgQteN?type=view#LMD-GHOST-fork-choice-rule) is the key here - It decides which of the available chains is the canonical one.

![](.gitbook/assets/image%20%28102%29.png)

## **Validator Lifecycle**

#### **1. Deposited** 

* 32 ETH has been deposited to the ETH1 deposit-contract and this state will be kept for around 7 hours. This offers security in case the ETH1 chain gets attacked.

#### **2. Pending**

Waiting for activation on ETH2

* Until 327680 active validators in the network, **4 validators can be activated per epoch**.  For every **65536** \(=4 \* 16384\) active validator, the validator **activation rate** goes up by one. 5 validators per epoch requires 327680 active validators. 
* Amount of activations scales with the amount of active validators and the limit is the active validator set divided by 64.000

#### **3. Active Validator** 

Currently attesting and proposing blocks **\(=block proposer\)**.

The validator will stay active until:

* its balance drops below 16 ETH \(ejected\).
* voluntary exit
* it gets slashed

#### **4. Slashing Validator** 

The Validator has been malicious and will be slashed and kicked out of the system

> A _**Penalty**_ is a negative reward \(e.g. for going offline\).   
> A _**Slashing**_ is a large penalty \(≥ 1/32 of balance at stake**\)** and a forceful exit ... **. - Justin Drake**

  
**5. Exiting Validator**

* **Ejected**  The validator balance fell below a threshold and was kicked out by the network 
* **Exited**  Voluntary exit, the withdrawal key holder has the ability to **withdraw** the current balance of the corresponding validator balance.

## Finalization

In Ethereum 2.0 **at least two third of the validators have to be honest**, therefore if there are two competing Epochs and one third of the validators decide to be malicious, they will receive a penalty. Honest ones will be rewarded.

In order to determine if an Epoch has been finalized, validators have to agree on the latest two epochs in a row \(= “justified”\) then all previous Epochs can be considered as finalized.

![](https://user-images.githubusercontent.com/26490734/73467349-81761e00-4383-11ea-8733-af69fa72ebf6.png)

