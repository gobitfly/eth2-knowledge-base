---
description: Altona Testnet
---

# Beaconnode & validator with macOS

[Official Lighthouse docs  
](https://lighthouse-book.sigmaprime.io/become-a-validator-source.html)[Lighthouse Discord server](https://discord.gg/8mFMS7G)

#### Requirements:  A synced Goerli node \([Guide](https://kb.beaconcha.in/run-a-goerli-node-eth1-and-beaconnode-eth2#step-1) till step 3.\)

#### 

#### 1. Step 

#### Installing Rust

Open a terminal window and paste the following in:

`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

_"Current installation options"_  
Press **"1"** and confirm with Enter.

![](../../.gitbook/assets/image%20%28130%29.png)

_"Next time you log in this will be done automatically"_  
**Close** this terminal window and **open a new one.**

#### 2. Downloading and building Lighthouse

`git clone https://github.com/sigp/lighthouse.git  
cd lighthouse`

and then run `make`

![](../../.gitbook/assets/image%20%28133%29.png)

_Wait a few minutes_  
Once the process is done it will look like the following

![](../../.gitbook/assets/image%20%28128%29.png)

#### 3. Find the binary file

Open **Finder** and head over to `~/.cargo/bin/`

![](../../.gitbook/assets/image%20%28132%29.png)

**Copy** the Lighthouse file to a more convenient folder.

#### 4. Start the beaconnode

Drag and drop the **Lighthouse** file and add `bn --eth1-endpoint http:127.0.0.1:8545 --http`

![](../../.gitbook/assets/lhsync.gif)

#### 

#### 5. Create ETH2 Wallet

_**Lighthouse** allows you to create an ETH2 wallet and attach your validator keys._

Open a new Terminal window, drag and drop the Lighthouse file and **add**  
`lighthouse account wallet create --name my-validators --passphrase-file my-validators.pass`

**The 12 word mnemonic phrase can restore the ETH2 wallet - write the words down.**

![](../../.gitbook/assets/image%20%28134%29.png)

The wallet is located in `$HOME/lighthouse`

![](../../.gitbook/assets/image%20%28123%29.png)

#### 6. Create ETH2 Keys

Use the same Terminal window, drag and drop the Lighthouse file and **add**   
`lighthouse account validator create --wallet-name my-validators --wallet-passphrase my-validators.pass --count 1`

![](../../.gitbook/assets/image%20%28131%29.png)

#### 7. Depositing to Ethereum 2.0

First, find the newly created ETH2 Key its deposit data, which is located in `.lighthouse/validators/`   
  
There are two lighthouse folders, `.lighthouse` is a hidden folder.  
**Enable hidden folders with** **`CMD + Shift + .`**

Open the `eth1-deposit-data.rlp` file with a **text editor.   
Copy** the 842 long text sequence and **follow these** [**steps**](https://kb.beaconcha.in/ethereum-2.0-and-depositing-process/depositing-to-ethereum-2.0#depositing)**.  
  
Altona Deposit contract address:** `0x16e82D77882A663454Ef92806b7DeCa1D394810f`

The deposit will be recognised by the beacon-chain in 8hours.

![](../../.gitbook/assets/image%20%28127%29.png)



#### 8. Starting the validator

Open a new terminal window, drag and drop the **Lighthouse** file and add `validator --auto-register`

In total there are **three** terminal windows running simultaneously!   
[Track](https://altona.beaconcha.in/dashboard?validators=) your validator performance.

![](../../.gitbook/assets/image%20%28122%29.png)







