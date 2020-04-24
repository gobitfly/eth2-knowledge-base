# Installing Docker on Windows Home

#### **Installing Docker on Windows Home**

**Step 0.**

Make sure you have [Windows10 Home](https://support.microsoft.com/en-us/help/13443/windows-which-version-am-i-running).

Since Docker is usually not available for Windows 10 Home some workaround are required as mentioned below.

**Step 1.**

[Download Docker](https://download.docker.com/win/stable/40693/Docker%20Desktop%20Installer.exe) \(do not install yet\). _\(What is_ [_Docker_](https://docs.docker.com/docker-for-windows/install/)_?\)_

Install [Hyper-V](https://www.deskmodder.de/blog/wp-content/uploads/2018/08/hyper-v-installer-1.zip) by running the **.bat** file. [_source_](https://www.deskmodder.de/blog/2018/08/23/windows-10-home-hyper-v-aktivieren/)\_\_

You will need to have [Virtualization](https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization-must-be-enabled) enabled, which you can check in the Taskmanager.

![virtualization](https://user-images.githubusercontent.com/26490734/79853838-dba5de80-83c8-11ea-9fbf-d640c4bb1980.png)

**Step 2.**

Because Docker is not available for Windows10 Home, we need to act like a Windows10 Pro user:

Open the "Registry Editor" and go the following path \(picture below\):

`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion`

**change** `EditionID` to `Professional` and `ProductName` to `Windows 10 Pro`

**immediately** open the downloaded Docker File and **install Docker**.

![registryEditor](https://user-images.githubusercontent.com/26490734/80191362-dbe6e980-8615-11ea-9633-3de4909a997d.png)

\(In case of a **PC restart, shutdown or Docker shutdown**, the registry change above needs to be re-entered otherwise Docker will not start\)

**Step 3.**

Change Docker File sharing settings - Manually create a folder called **"prysm"** in that specific directory. Picture below for clarification.

![dockerWindows](https://user-images.githubusercontent.com/26490734/79551080-7c2e9280-8099-11ea-8886-0b739b7d12c1.png)

**Step.4**

Change Docker's default memory to 4GB

![dockerMemory](https://user-images.githubusercontent.com/26490734/80192514-9aefd480-8617-11ea-93b4-e709a988a5c0.png)

