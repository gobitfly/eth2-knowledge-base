# Run a Slasher using prysm.sh

## General

The slasher's purpose is to find malicious validators **in the Ethereum 2.0 network** and report slashable offenses to the beacon-node.  
****

![](../../.gitbook/assets/image%20%2869%29.png)

#### 

## How does the slasher work?

The s**lasher is its own entity** which allows the user to run the slasher independently without the need of a local beaconnode or validator.  
  
To find malicious activity by validators, the slashers receives all attestations from beacon-nodes and iterates through them until a **slashable offense** has been found.   
The slasher then sends proof to beacon-nodes which includes 

## Run a slasher

Make sure your **beaconnode** is **in sync** and running along with a **validator**.   
If you need to make up for it, please look [here for windows](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/windows-prysm/script-beaconnode-and-validator) and [here for macOS](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/macos-prysm/run-with-macos-using-prysm.sh).

