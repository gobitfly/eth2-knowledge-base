# Run a Slasher using prysm.sh

## General

The slasher's purpose is to find malicious validators **in the Ethereum 2.0 network** and report slashable offenses to the beacon-node.  
****

![](../../.gitbook/assets/image%20%2869%29.png)

#### 

## How does the slasher work?

The s**lasher is its own entity** but requires a beacon-node to receive attestations from.  
To find malicious activity by validators, the slashers iterates through all received attestations until a **slashable offense** has been found. The slasher then **sends proof** to beacon-nodes which includes it into the next block and the malicious validator gets slashed.

## Run a slasher

Make sure your **beaconnode** is **in sync**.   
If you haven't done so already, please look [here for windows](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/windows-prysm/script-beaconnode-and-validator) and [here for macOS](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/macos-prysm/run-with-macos-using-prysm.sh).  


####  **Step 1.**

Drag and drop the **prysm.sh** file into the **Terminal** window and add:

`slasher  --datadir=$HOME/prysm`

![](../../.gitbook/assets/slashergif.gif)



**That's it!**  
The slasher now iterates through all attestations and sends proof to the detection service.   
  
Debug mode enabled with `--verbosity=debug`

![](../../.gitbook/assets/image%20%2871%29.png)

