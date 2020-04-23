# Run with Windows w/Docker

####  [Offcial **PrysmaticLabs Docs**](https://docs.prylabs.network/docs/getting-started/)\*\*\*\*

**Step 0.**

Start Docker and open a [Command Prompt](https://www.wikihow.com/Open-the-Command-Prompt-in-Windows) window and type `docker -v`. If installed correctly it should give you the Docker Version. If not, please make sure to follow the steps in **Installing Docker on Windows Pro/Home**.

If successful, you can run the following code:

`reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1`

{% hint style="info" %}
 **this is not required but changes the look of your command prompt output**
{% endhint %}



To get the latest testnet client version & starting the beaconchain follow up with this:

**Pull latest beaconchain updates:**

`docker pull gcr.io/prysmaticlabs/prysm/beacon-chain:latest`

![dockerPull](https://user-images.githubusercontent.com/26490734/79550092-2efdf100-8098-11ea-948f-84cc150a2251.png)

**Pull latest validator updates:**

`docker pull gcr.io/prysmaticlabs/prysm/validator:latest`

**Starting the beaconchain:**

`docker run -it -v c:/prysm/:/data -p 4000:4000 -p 13000:13000 gcr.io/prysmaticlabs/prysm/beacon-chain:latest --datadir=/data`

{% hint style="info" %}
The blockchain data will be stored in the manually created folder **\(Docker installation chapter\).**\(C:\prysm\).
{% endhint %}

**Wait** for your beacon-node to be in sync with the Blockchain.   
This may take a few hours. You will see the following message:

`INFO initial-sync: Synced up to slot XXXXX` 

![](../../.gitbook/assets/image%20%283%29.png)

**Creating your ETH2 Keys:**

Copy the following code:

`docker run -it -v c:/prysm:/data gcr.io/prysmaticlabs/prysm/validator:latest accounts create --keystore-path=/data --password=yourPassword`

Once you press enter the output should look the image below.   
If you didn't change `--password=yourPassword` your validator keys will have this password by default.   
For simplicity, let's keep it this way for the testnet.

`C:\prysm` is the location of your keys - make sure they are available.

**Copy the Raw Transaction Data** and go to the [participation page](https://prylabs.net/participate).

![keyCreation](https://user-images.githubusercontent.com/26490734/79857621-59b8b400-83ce-11ea-9bb5-6b5f0ba9ac7e.png)

**Step 2.**

Get 32 Goerli ETH \(=Testnet ETH\). If you cannot get any goerli ETH through the participation page, join the [Prysm Discord](https://discord.gg/wJW7Rjk) Follow the steps below to deposit your goerli ETH.

![Participation](https://user-images.githubusercontent.com/26490734/79573699-53b98f00-80bf-11ea-8c7c-4092778bab7d.png)

**Step 3.**

Starting the validator.

Open **a new** command prompt window.

**Start your validator**

`docker run -it -v c:/prysm:/data --network="host" gcr.io/prysmaticlabs/prysm/validator:latest --beacon-rpc-provider=127.0.0.1:4000 --keystore-path=/data --datadir=/data --password=yourPassword`

**Step 4.**

Track your validator performance on [beaconcha.in](https://beaconcha.in/dashboard?validators=) with your public key \(orange\).

You will need to wait for the inclusionSlot \(red\) to be reached until your deposit is recognized by the system and to start staking. The Slot number can be checked [here](https://beaconcha.in/blocks).

![Validator&amp;beaconcha.in](https://user-images.githubusercontent.com/26490734/79860463-fda45e80-83d2-11ea-8b71-05a112117f18.png)

**Running multiple validators \(voluntarily\)**

Repeat  **Step 2.** and **create more keys** in the same directory \(USE THE SAME PASSWORD FOR ALL\).

Copy the **Raw Transaction Data** for each validator and re-do the process on the [participation page](https://prylabs.net/participate) and deposit for each of them.

After all deposits have been received by the system, you can just start a single validator window and it will use **all** the created keys \(=multiple validators\).

