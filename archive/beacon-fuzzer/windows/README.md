---
description: Beacon Fuzzer guide for windows users.
---

# Fuzzing on Windows

### General

[_**Fuzzing**_](https://en.wikipedia.org/wiki/Fuzzing) _or **fuzz testing** is an automated software testing technique that involves providing invalid, unexpected, or random data as inputs to a computer program._

* [https://github.com/sigp/beacon-fuzz](https://github.com/sigp/beacon-fuzz)
* [Lighthouse Discord Channel](https://discord.gg/Xdc9xZX)

#### Requirements

* Install **Docker** on [Windows Pro](https://kb.beaconcha.in/beacon-fuzzer/windows/installing-docker-on-windows-pro) or [Windows Home](https://kb.beaconcha.in/beacon-fuzzer/windows/installing-docker-on-windows-home)
* Install **MAKE** for Windows (External [Video Guide](https://www.youtube.com/watch?v=sXW2VLrQ3Bs) & [StackOverflow](https://stackoverflow.com/a/32127632))
* 8-16 GB RAM&#x20;
* 2-4 Core CPU\


### Download the Fuzzer

#### Step 0.&#x20;

Open a **terminal window** and test if docker is up and running with **** `docker -v`

#### **Step 0.**

Continue with **** `cd desktop` **** followed by **** `git clone https://github.com/sigp/beacon-fuzz`

![](<../../../.gitbook/assets/image (150).png>)

###

### Edit the MAKE file

Head over to the desktop and open the downloaded folder `beacon-fuzz` .\
Continue to the subfolder `eth2fuzz` and open the `Makefile` file with **a text editor**.

Replace all `DOCKER_BUILDKIT=1` in the **Makefile** with `docker build \` and **save** the changes.\
There are five **"DOCKER\_BUILDKIT=1"** in total. \
\
Alternatively, copy this [file](https://gist.github.com/Buttaa/7493f747f673f513eb5c60b20661e780), which has everything replaced.

![](<../../../.gitbook/assets/image (149).png>)



### Fuzzing

#### Step 0.

Open a **terminal window** and go to the eth2fuzz directory with \
****`cd desktop/beacon-fuzz/eth2fuzz`

#### Step 1.

Build all clients and start fuzzing by running `make fuzz-all`

That's it, the process will take multiple hours!

![](<../../../.gitbook/assets/image (152).png>)

### Report Bugs

Search the `beacon-fuzz` folder for files called "_**crash-..."**_, which is the bug file, and compress it \
to a **zip file.** \
****[Web tool](https://archive.online-convert.com/convert-to-zip) to convert files into zip.\
\
**Post the zip file on the beacon-fuzz** [**github repository**](https://github.com/sigp/beacon-fuzz/issues/new/choose)**.**

An example:\
_****`crash-efc8b3f0753ddd9df52b066d2f4549d548a21a58`_

![](<../../../.gitbook/assets/image (151).png>)



