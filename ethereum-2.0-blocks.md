---
description: Blocks 'n' roots
---

# Blocks

**WORK IN PROGRESS**  
  
_This post is going to explain the data Ethereum 2.0 explorers visualize such as_ [_beaconcha.in_](https://beaconcha.in/)\_\_

## Overview

_Epoch, Slot, Status, Proposer are covered in the_ [_glossary_](https://kb.beaconcha.in/glossary)  


### Block root

The hash-tree-root of the [BeaconBlock](https://github.com/ethereum/eth2.0-specs/blob/dev/specs/phase0/beacon-chain.md#beaconblock).

### State root

The hash-tree-root of the [BeaconState](https://github.com/ethereum/eth2.0-specs/blob/dev/specs/phase0/beacon-chain.md#beacon-state).

### Signature

The BLS signature [obtained by](https://github.com/ethereum/eth2.0-specs/blob/dev/specs/phase0/validator.md#packaging-into-a-signedbeaconblock) using the BeaconState, BeaconBlock and private key.

`def get_block_signature(state: BeaconState, block: BeaconBlock, privkey: int)   
-> BLSSignature`

### Randao Reveal

### Grafitti

A block proposer can include 32 byte long message to its block proposal.

### Eth 1 Data

_Received Eth1 Block headers and Deposit data_ 

* Block Hash: The hash of the
* Deposit Count
* Deposit Root

### Attestations

### Deposits

### Voluntary Exits

### Slashings 

![](.gitbook/assets/image%20%28176%29.png)

##  Votes



![](.gitbook/assets/image%20%28177%29.png)

## Attestations

### Slot

### Committee Index

### Aggregation Bits

### Validators

### Beacon Block Root

### Source  Target

### Signature

![](.gitbook/assets/image%20%28175%29.png)

