# Installing Docker on Windows Home

#### **Installing Docker on Windows Home**

**Step 0.**

Make sure you have [Windows10 Home](https://support.microsoft.com/en-us/help/13443/windows-which-version-am-i-running).

Since Docker is usually not available for Windows 10 Home some workaround are required as mentioned below.

\*\*\*\*

**Step 1.**

[Download Docker \(do not install yet\)](https://download.docker.com/win/stable/40693/Docker%20Desktop%20Installer.exe). \(What is [Docker](https://docs.docker.com/docker-for-windows/install/)?\)

Install [Hyper-V](https://www.deskmodder.de/blog/wp-content/uploads/2018/08/hyper-v-installer-1.zip) by running the .bat file. [_source_](https://www.deskmodder.de/blog/2018/08/23/windows-10-home-hyper-v-aktivieren/)\_\_

You will need to have [Virtualization](https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization-must-be-enabled) enabled, which you can check in the Taskmanager.

![virtualization](https://user-images.githubusercontent.com/26490734/79853838-dba5de80-83c8-11ea-9fbf-d640c4bb1980.png)

\*\*\*\*

**Step 2.**

Because Docker is not available for Windows10 Home, we need to act like a Windows10 Pro user:

Run the following code in a command prompt window

`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion`

**change** `EditionID` to `Professional` and `ProductName` to `Windows 10 Pro`

**immediately** open the downloaded Docker File and **install Docker**.

\(In case of a **PC restart, shutdown or Docker shutdown**, the code above needs to be re-entered otherwise Docker will not start\)



**Step 3.**

Change Docker File sharing settings - Manually create a folder called **"prysm"** in that specific directory. Picture below for clarification.

![dockerWindows](https://user-images.githubusercontent.com/26490734/79551080-7c2e9280-8099-11ea-8886-0b739b7d12c1.png)



