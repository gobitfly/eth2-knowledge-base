# Glossary

## Beacon Chain
 
It introduces Proof of stake to Ethereum1 and runs along it. It’s also called the coordination layer.

**Roles**:

  * Creating committees
  
  * Creation of randomness 
  
  * Manages rewards, penalties and validators
  
  * Responsible for timing (Slots & Epochs) 


## Slots (32 slots = 1 Epoch) 
A time period of **12 seconds** in which a randomly chosen validator has time to propose a block.
Each slot may or may not have a block in it. 
Slots play an important role since validators are assigned to slots and each of these then represent one or more committee per Epoch. One validator from the committee will be chosen to propose a block, while the other 127 are attesting. After each Epoch, the validators are mixed and merged to new committees (minimum of 128 validators per committee).

<img width="717" alt="validator" src="https://user-images.githubusercontent.com/26490734/73458538-bd09eb80-4375-11ea-83a1-27b5fb1394a1.png">

###### [image source](https://medium.com/coinmonks/eth2-0-phase-0-basics-for-new-contributors-8a0a22bc38c7)  

## Epoch

Represents the number of slots and takes approximately **6.4 minutes** and consists of 32 Slots (12 seconds each).


## Validator 
Each validator equals 32 ETH which was deposited into the validator-deposit-contract on the ETH1 chain and requires the user 
to run a validator node. Their job is to propose blocks and attestations.


**Validator Lifecycle:**
	
**1. Deposited:**
  32 ETH has been deposited to the ETH1 and this state will be kept for around 7 hours. 
  This offers security in case the ETH1 chain gets attacked.
      
      
**2. Pending: Waiting for activation on ETH2**
  * A minimum of 4 validators per Epoch can be activated. (900 per day)
  * Amount of activations scales with the amount of active validators 
    and the limit is the active validator set divided by 64.000
  * 900 validators can be activated per day until 327680 active validators have been reached. 
    Then it becomes 5 per epoch
    
              
**3. Active Validator:**
Currently attesting and proposing blocks **(=proposer)**. 

  The Validator will stay active until:
  * the balance drops below 16 ETH
  * voluntary exit
  * slashed
  
**4. Slashing Validator: The Validator has been malicious.**


![slashed](https://user-images.githubusercontent.com/26490734/73463604-d44cd700-437d-11ea-9c11-a2fed18fdc6d.png)



**5. Exiting Validator:**

  * Ejected: the validator balance fell below a threshold and was kicked out by the network
  * Exited: voluntary exit
  
  
## Block proposer

A validator which was chosen by the beacon chain to propose the next block. There is only one per slot. 

## Attestations: 

Votes by validators which confirm the validity of a block.

## Unique Index:

An identifier for validators, as seen on [beaconcha.in](https://www.beaconcha.in/) or [beacon.etherscan.io](https://beacon.etherscan.io/)

![index](https://user-images.githubusercontent.com/26490734/73463991-7a004600-437e-11ea-9ddb-78aa30f2d1ae.png)


**Eligible for activation & Estimated activation:**

Refers to pending validators. The deposit has been recognized by the ETH2 chain at the timestamp of “Eligible for activation”.
If there is a queue of [pending validators](https://www.beaconcha.in/validators) an estimated timestamp for activation will be calculated.


**Current Balance & Effective Balance:**

The current balance is the amount of ETH which is being held by the validator as of now. 
The effective Balance represents a value calculated by the current balance. It is used to determine the size of a reward or penalty a validator receives. The effective balance can **never be higher than 32 ETH.** 

Here are examples on how the effective balance is calculated:

  *Current balance: 32.00 ETH – Effective balance: 32.00 ETH
  
  *Current balance: 30.50 ETH – Effective balance: 30.00 ETH
  
  *Current balance: 29.99 ETH – Effective balance: 29.00 ETH
  
**In order to increase the effective balance, the validator requires “effective balance + 1.5 ETH”.**
In other words, if your effective balance is 20 ETH, you will need a current balance of 
21.5 ETH in order to have an effective balance of 21 ETH.


## Finalization

In Ethereum 2.0 **at least two third of the validators have to be honest**, therefore if there are two competing Epochs and one third of the validators decide to be malicious, they will receive a penalty. Honest ones will be rewarded. 

In order to determine if an Epoch has been finalized, validators have to agree on the latest two epochs in a row (= “justified”) then all previous Epochs can be considered as finalized.

![finalization](https://user-images.githubusercontent.com/26490734/73467349-81761e00-4383-11ea-8733-af69fa72ebf6.png)


## Block status 

  * Proposed: The block passed and was proposed by a validator.
  
  * Scheduled: Validators are currently submitting data.
  
  * Missed/Skipped: The proposer didn’t propose the block within the given time frame, so the block was missed/skipped. 

  * Orphaned: In order to understand this easily we look at the diagram below: (the numbers "1, 2, 3,  ... ,9" represent the                    number of the slots).
  
  
  1. Validator at slot 1 proposes the block “a”.
  2. Validator at slot 2 proposes “b”.
  3. Validator 3 proposes “c”. 
  4. Slot 4 is being skipped because the validator didn’t propose a block (e.g.: offline).
  5. At slot 5/6 a fork occurs: Validator(5) proposes a block, but validator(6) doesn’t receive this data (e.g.: the block          didn’t reach them fast enough). Therefore Validator(6) proposes its block with the most recent information it sees from 
     validator(3). 
  6. The [fork choice rule](https://notes.ethereum.org/@vbuterin/rkhCgQteN?type=view#LMD-GHOST-fork-choice-rule) is the key         here which decides which one of the available chains is the canonical one.
	
![image](https://user-images.githubusercontent.com/26490734/73468330-e67e4380-4384-11ea-81cd-cb18d7a88e92.png)
