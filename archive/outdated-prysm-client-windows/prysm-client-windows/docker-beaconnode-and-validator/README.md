# Beaconnode & validator using Docker

####  [Official **PrysmaticLabs Docs**](https://docs.prylabs.network/docs/getting-started/)\*\*\*\*

{% hint style="info" %}
A folder named "prysm" in C:\ needs to be created which will also be the location of the beaconchain data.
{% endhint %}

![prysmFolder](https://user-images.githubusercontent.com/26490734/80280580-2e530380-8705-11ea-9574-49b345376844.png)

#### **Step 0.**

Start Docker, open a [Command Prompt](https://www.wikihow.com/Open-the-Command-Prompt-in-Windows) window and type `docker -v`. If Docker is installed correctly, it will return you the Docker Version. If not, please make sure to follow the steps in [_**Installing Docker on Windows Pro**_](https://kb.beaconcha.in/tutorial-eth2-multiclient/docker-beaconnode-and-validator/installingdocker) **if you are on the professional version and** [_**Installing Docker on Windows Home**_](https://kb.beaconcha.in/tutorial-eth2-multiclient/docker-beaconnode-and-validator/installdocker) **if you are on the home version**.

If the previous command was successful, run the following code:

`reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1`

{% hint style="info" %}
 **This is not required. By using this command, cosmetics of the command prompt window change.**
{% endhint %}

#### **Step 1.**

**Download and install latest beaconchain updates**

`docker pull gcr.io/prysmaticlabs/prysm/beacon-chain:latest`

![dockerPull](https://user-images.githubusercontent.com/26490734/79550092-2efdf100-8098-11ea-948f-84cc150a2251.png)

#### **Download and install latest validator updates**

`docker pull gcr.io/prysmaticlabs/prysm/validator:latest`

#### **Create a docker network** 

`docker network create --attachable medalla`

#### **Start the beaconnode**

`docker run -ti --name beacon-chain --network medalla -v c:/prysm:/data -p 12000:12000/udp -p 13000:13000 gcr.io/prysmaticlabs/prysm/beacon-chain:latest --datadir=/data --rpc-host=0.0.0.0`

**Wait** for your beaconnode to be in sync with the blockchain.   
This may take a few hours and you will see the following message:

`INFO initial-sync: Synced up to slot XXXXX` 

![](../../../../.gitbook/assets/image%20%2827%29.png)

#### **Step.2**

**Create ETH2 keys**

`docker run -it -v c:/prysm:/data gcr.io/prysmaticlabs/prysm/validator:latest accounts create --keystore-path=/data --password=yourPassword`

The output should look like the image below.   
If you didn't change `--password=yourPassword` , your validator keys will have **yourPassword** as its password.  
The newly created keys should be in `C:\prysm`. Make sure they are available.

**Copy the Raw Transaction Data** and go to the [participation page](https://prylabs.net/participate). 

![keyCreation](https://user-images.githubusercontent.com/26490734/79857621-59b8b400-83ce-11ea-9bb5-6b5f0ba9ac7e.png)

#### **Step 3.**

Some of the instructions on the **participation page** will be ignored because they were not optimized for Windows10 \(yet\).   
  
Follow the steps below to get Goerli ETH and to deposit them to activate your validator. If you cannot get any Goerli ETH through the participation page, join the [Prysm Discord](https://discord.gg/wJW7Rjk) channel.

![](../../../../.gitbook/assets/image%20%286%29.png)

#### **Step 4.**

Open **a new** command prompt window.

**Start your validator**

`docker run -ti -name validator --network medalla -v c:/prysm:/data gcr.io/prysmaticlabs/prysm/validator:latest --keystore-path=/data --datadir=/data --password=yourPassword --medalla --beacon-rpc-provider=beacon-chain:4000` 

#### **Step 5.**

Track your validator performance on [beaconcha.in](https://beaconcha.in/dashboard?validators=) with your public key \(orange\).   
Once the blockchain recognises the deposit, the [beaoncha.in](https://beaconcha.in/) explorer will allow you to track the validator more accurately.

Wait for the inclusionSlot \(red\) to be reached. Once the blockchain has processed this slot, you will be staking! The Slot number can be tracked [here](https://beaconcha.in/blocks).

![Validator&amp;beaconcha.in](https://user-images.githubusercontent.com/26490734/79860463-fda45e80-83d2-11ea-8b71-05a112117f18.png)

#### **Running multiple validators \(voluntarily\)**

Repeat **Step 2.** and **create more keys** into the same directory.   
**Use the same password for all keys.**

Copy the **Raw Transaction Data** for each validator, re-do the process on the [participation page](https://prylabs.net/participate) and deposit for each of them.

Once the system has received all deposits, you can just start a single validator window, and it will use **all** of the created keys \(=multiple validators\).

{% hint style="info" %}
For further assistance, please join the Prysmatic Labs Discord [channel](https://discord.gg/wJW7Rjk).
{% endhint %}

