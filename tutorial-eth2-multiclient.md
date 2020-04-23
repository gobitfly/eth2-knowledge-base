# Step by Step: How to use the Ethereum 2.0 Multiclient

This guide will be designed for **non technical** people. It will focus on **Windows10 and MacOs**. 

It be an ongoing process and will be updated as we collect feedback and adapt to the most recent changes! 

There are **multiple ways** to join the ETH2.0 Testnet (different clients).

**System requirements: Recommended: 8GB RAM, 100GB SSD , Minimum: 4GB RAM, 20GB SSD.**

Before we start off, reading the [glossary](https://kb.beaconcha.in/glossary) is recommended but not required.

---

### Overview

#### [Prysmatic Labs](https://docs.prylabs.network/docs/getting-started/)

- Windows 10

    - - [Installing Docker on Windows Home](#installWindowsHome)
    - - [Installing Docker on Windows Pro](#installWindowsPro)
    - [Run with Windows **Pro & Home** w/Docker](#runWithDocker)
    - [Windows 10 w/Binary files (.exe)](#runWithBinary) 
    - [Prysm.sh script](#runWithScript)
    
- macOS

    - Docker (soon)
    - Prysm.sh script (soon)
    
#### [Lighthouse](https://lighthouse.sigmaprime.io/) <ins> waiting for client release </ins>

- Windows 10

    - Windows 10 w/Binary files (.exe) (soon)
    - Windows **10 Pro** w/Docker (soon)
    - script (soon)
  
---
### [Prysmatic Labs - Topaz Testnet](https://prysmaticlabs.com/)

#### <a name="installWindowsHome"></a> Installing Docker on Windows **Home**

<details>

<ins>**Step 0.**</ins>

Make sure you have [Windows10 Home](https://support.microsoft.com/en-us/help/13443/windows-which-version-am-i-running).

Since Docker is usually not available for Windows 10 Home some workaround are required as mentioned below.

<ins>**Step 1.**</ins>

[Download Docker (do not install yet)](https://download.docker.com/win/stable/40693/Docker%20Desktop%20Installer.exe). <sup> [Docker Info](https://docs.docker.com/docker-for-windows/install/) </sup>

Install [Hyper-V](https://www.deskmodder.de/blog/wp-content/uploads/2018/08/hyper-v-installer-1.zip) by running the .bat file. <sup> [source](https://www.deskmodder.de/blog/2018/08/23/windows-10-home-hyper-v-aktivieren/) </sup>

You will need to have "[Virtualization](https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization-must-be-enabled)" enabled, which you can check in the Taskmanager. 

<details>
  <summary>Virtualization enabled</summary>
  
![virtualization](https://user-images.githubusercontent.com/26490734/79853838-dba5de80-83c8-11ea-9fbf-d640c4bb1980.png)
</details>

<ins>**Step 2.**</ins>

Because Docker is not available for Windows10 Home, we need to act like a Windows10 Pro user:

Run the following code in a command prompt window 

`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion`

**change** `EditionID` to `Professional` and `ProductName` to `Windows 10 Pro`

**immediately** open the downloaded Docker File and **install Docker**. 

(In case of a **PC restart, shutdown or Docker shutdown**, the code above needs to be re-entered otherwise Docker will not start)

<ins>**Step 3.**</ins>

Change Docker File sharing settings - Manually create a folder called **"prysm"** in that specific directory. Picture below for clarification.

<details>
  <summary>Picture to clarify</summary>
  
 ![dockerWindows](https://user-images.githubusercontent.com/26490734/79551080-7c2e9280-8099-11ea-8886-0b739b7d12c1.png) 
</details>

</details>

---

#### <a name="installWindowsPro"></a> Installing Docker on Windows **Pro**

<details>

<ins>**Step 0.**</ins>

Make sure you have [Windows10 Pro](https://support.microsoft.com/en-us/help/13443/windows-which-version-am-i-running)

<ins>**Step 1.**</ins>

[Download Docker](https://download.docker.com/win/stable/Docker%20Desktop%20Installer.exe). Installing is different for everyone depending on the motherboard manufacturer. Entering BIOS may be required to change "virtualization" to "enabled".

You will need to have "[Virtualization](https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization-must-be-enabled)" enabled, which you can in the Taskmanager. <sup> [Docker Info Page](https://docs.docker.com/docker-for-windows/install/) </sup>

<details>
  <summary>Virtualization enabled</summary>
  
![virtualization](https://user-images.githubusercontent.com/26490734/79853838-dba5de80-83c8-11ea-9fbf-d640c4bb1980.png)
</details>

<ins>**Step 2.**</ins>

Change Docker File sharing settings - Manually create a folder called **"prysm"** in that specific directory. Picture below for clarification.

<details>
  <summary>Picture to clarify</summary>
  
 ![dockerWindows](https://user-images.githubusercontent.com/26490734/79551080-7c2e9280-8099-11ea-8886-0b739b7d12c1.png) 
</details>

</details>

---

#### <a name="runWithDocker"></a> Run with Windows **Pro & Home** w/Docker

<details>

<ins>**Step 0.**</ins>

Start Docker and open a [Command Prompt](https://www.wikihow.com/Open-the-Command-Prompt-in-Windows) window and type `docker -v`. If installed correctly it should give you the Docker Version. If not, please make sure to follow the steps in **Installing Docker on Windows Pro/Home**.

If successful, you can run the following code **(this is not required but changes the look of your command prompt output)**: 

`reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1` 

To get the latest testnet client version & starting the beaconchain follow up with this:

1. Pull latest Beaconchain updates:

`docker pull gcr.io/prysmaticlabs/prysm/beacon-chain:latest`

<details>
  <summary>Picture to clarify</summary>
  
 ![pullValidator](https://user-images.githubusercontent.com/26490734/79550092-2efdf100-8098-11ea-948f-84cc150a2251.png)
</details>

2. Pull latest Validator updates: 

`docker pull gcr.io/prysmaticlabs/prysm/validator:latest`

3. Starting the beaconchain 

`docker run -it -v c:/prysm/:/data -p 4000:4000 -p 13000:13000 gcr.io/prysmaticlabs/prysm/beacon-chain:latest --datadir=/data`

<sub> The blockchain data will be stored in the folder we manually created in the **Docker installation** (C:\prysm). </sub>

**Wait** for your beacon-node to be in sync with the Blockchain. This may take a few hours. You will see the following message:

`INFO initial-sync: Synced up to slot XXXXX`

<details>
    <summary>Picture to clarify </summary>  
    
![synced](https://user-images.githubusercontent.com/26490734/79868679-8a094e00-83e0-11ea-81a0-d22ce4a741e9.png)
</details>

<ins>**Step 1.**</ins>

**Creating your ETH2 Keys:**

Copy the following code: 

`docker run -it -v c:/prysm:/data gcr.io/prysmaticlabs/prysm/validator:latest accounts create --keystore-path=/data --password=yourPassword`

Once you press enter the output should look the image below. If you didn't change `--password=yourPassword` your validator keys will have this password by default. For simplicity, let's keep it this way for the testnet.

`C:\prysm` is the location of your keys - make sure they are available.

**Copy the Raw Transaction Data** and go to the [participation page](https://prylabs.net/participate).

<details>
  <summary>Picture to clarify</summary>
  
![keyCreation](https://user-images.githubusercontent.com/26490734/79857621-59b8b400-83ce-11ea-9bb5-6b5f0ba9ac7e.png)
</details>

<ins>**Step 2.**</ins>

Get 32 Goerli ETH (=Testnet ETH). If you cannot get any goerli ETH through the participation page, join the [Prysm Discord](https://discord.gg/wJW7Rjk) Follow the steps below to deposit your Goerli ETH.

<details>
  <summary>Picture to clarify</summary>
  
![Participation](https://user-images.githubusercontent.com/26490734/79573699-53b98f00-80bf-11ea-8c7c-4092778bab7d.png)
</details>

<ins>**Step 3.**</ins>

Starting the validator. 

Open **a new** command prompt window.

**Start your validator**

`docker run -it -v c:/prysm:/data --network="host" gcr.io/prysmaticlabs/prysm/validator:latest --beacon-rpc-provider=127.0.0.1:4000 --keystore-path=/data --datadir=/data --password=yourPassword`

<ins>**Step 4.**</ins>

Track your validator perfomance on [beaconcha.in](https://beaconcha.in/dashboard?validators=) with your public key (orange). 

You will need to wait for the inclusionSlot (red) to be reached until your deposit is recognized by the system and to start staking. The Slot number can be checked [here](https://beaconcha.in/blocks)

<details>
  <summary>Picture to clarify</summary>
  
  ![Validator&beaconcha.in](https://user-images.githubusercontent.com/26490734/79860463-fda45e80-83d2-11ea-8b71-05a112117f18.png)

</details>

<ins>**Running multiple validators (voluntarily)**</ins>

<details>
    
Repeat <ins> **Step 2.** </ins> and **create more keys** in the same directory (USE THE SAME PASSWORD FOR ALL).

Copy the **Raw Transaction Data** for each validator and re-do the process on the [participation page](https://prylabs.net/participate) and deposit for each of them.

After all deposits have been received by the system, you can just start a single validator window and it will use all the created keys (=multiple validators)

</details>

</details>

---

#### <a name="runWithBinary"></a> Windows 10 w/Binary files (.exe) <ins> (currently not working - requires fix by PrysmaticLabs) </ins>

<details>

<ins>**Step 0.**</ins> 

Open the [Prysmatic Participation Page](https://prylabs.net/participate) and the [client release page](https://github.com/prysmaticlabs/prysm/releases)

<ins>**Step 1.**</ins> 

Open a [Command Prompt](https://www.wikihow.com/Open-the-Command-Prompt-in-Windows) window and enter the following:

`reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1`

<sub> This will change the looks of the command prompt output later </sub>

<ins>**Step 2.**</ins> 

**Download** the newest versions of the Beaconchain **and** Validator. The version name might have changed because of an update, but the file name should similar (green mark on the picture below).

<details>
  <summary>Picture to clarify</summary>
  
![Prysmatic_DownloadPage](https://user-images.githubusercontent.com/26490734/79451678-33b69c80-7fe7-11ea-80c8-b92c75fbb937.png)
</details>

<ins>**Step 3.**</ins> 

Find the files that have been downloaded. Usually located in the "Downloads" folder

<ins>**Step 4.**</ins> 

Open the beaconchain file - **beacon-chain**-v1.0.0-alpha.2-<ins>windows-amd64</ins>.exe - a **warnining** should appear. **Click** on "More Info" and then "Run anyway".

<details>
  <summary>Picture to clarify</summary>
  
![Prysmatic_DownloadWarning](https://user-images.githubusercontent.com/26490734/79451935-a1fb5f00-7fe7-11ea-875d-f443afe24b09.png) 
</details>

1. **If this does not work**, you can also open a "Command Prompt" window and drag&drop the beaconchain file into it and press enter.
2. **If you get the error** `The process cannot access the file because it is being used by another process`, you will need **manually** delete the "beaconchain.db" file.

#### Windows 10 w/Binary files (.exe) - <ins>Validator</ins> (REQUIRES [A FIX BY PRYSM TEAM](https://github.com/prysmaticlabs/prysm/issues/5456#issue-601128068))

<ins>**Step 0.**</ins> 

<!-- Make sure to have the Validator File as desribed [here, <ins>Step 1 and 2.</ins>](https://github.com/Buttaa/eth2-knowledge-base/blob/howToMultiClient/howToMulticlient.md#windows10) -->

<ins>**Step 1.**</ins> 

<!-- Open the validator file - **validator**-v1.0.0-alpha.2-<ins>windows</ins>-amd64 -->

</details>

---

#### <a name="runWithScript"></a> Run with Prysm.sh script <ins> (currently not working - requires fix by PrysmaticLabs) </ins>

<details>
</details>
