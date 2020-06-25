# Essential commands \(macOS & Windows\)

#### A summary of the most important flags to run the prysm client with **prysm.sh** or **prysm.bat.**  For beginner friendly guides please look [here for Windows](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/windows-prysm/script-beaconnode-and-validator) and [here for macOS](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/macos-prysm/run-with-macos-using-prysm.sh).

## Windows

**Get prysm.bat file**  
`curl https://raw.githubusercontent.com/prysmaticlabs/prysm/master/prysm.bat --output prysm.bat`

**Beacon-node**  
`prysm.bat beacon-chain --datadir=$HOME/prysm`

**Create new keys**`prysm.bat validator accounts create --keystore-path=$HOME/prysm --password=yourPassword`

**Validator**  
`prysm.bat validator --keystore-path=$HOME/prysm --password=yourPassword`  
  
**Slasher**  
`prysm.bat slasher --datadir=$HOME/prysm`

## macOS

**Get pryms.sh file**  
`curl https://raw.githubusercontent.com/prysmaticlabs/prysm/master/prysm.sh --output prysm.sh && chmod +x prysm.sh`

**Beacon-node**  
`prysm.sh beacon-chain --datadir=$HOME/prysm`

**Create new keys**`prysm.bat validator accounts create --keystore-path=$HOME/prysm --password=yourPassword`

**Validator**  
`prysm.sh validator --keystore-path=$HOME/prysm --password=yourPassword`  
  
**Slasher**  
`prysm.sh slasher --datadir=$HOME/prysm`

