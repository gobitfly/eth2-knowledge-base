# Run with macOS using docker

####  [Official **PrysmaticLabs Docs**](https://docs.prylabs.network/docs/getting-started/)\*\*\*\*

#### Step 0. 

[Install docker ](https://docs.docker.com/docker-for-mac/install/)

Step 1.

Check if **Docker** is installed through the terminal.   
This can be done by pressing `CMD+Space` and searching for **Terminal**.

Run `docker -v` .  
If the output returns the docker version, Docker is installed correctly.

![](../.gitbook/assets/image%20%2813%29.png)

**Step 1.**

**Download and install latest beaconchain updates**

`docker pull gcr.io/prysmaticlabs/prysm/beacon-chain:latest`

**Download and install latest validator updates**

`docker pull gcr.io/prysmaticlabs/prysm/validator:latest`

![](../.gitbook/assets/image%20%285%29.png)

\*\*\*\*

**Start the beaconnode**

`docker run -it -v $HOME/prysm:/data -p 4000:4000 -p 13000:13000 --name beacon-node \gcr.io/prysmaticlabs/prysm/beacon-chain:latest  --datadir=/data`

![](../.gitbook/assets/image%20%284%29.png)

The directory `$HOME/prysm` contains all the beaconchain data and can be accessed through **Finder.**

![](../.gitbook/assets/image%20%2815%29.png)

**Wait** for the beaconnode to be in sync with the blockchain.   
This may take a few hours and you will see the following message:

`INFO initial-sync: Synced up to slot XXXXX`

![](../.gitbook/assets/image.png)

\*\*\*\*

**Step 2.**

**Create ETH2 Keys**

Open a **new Terminal** window.

