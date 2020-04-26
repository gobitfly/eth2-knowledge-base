# Installing Docker on Windows Home

#### **Installing Docker on Windows Home**

**Step 0.**

Make sure you have [Windows10 Home](https://support.microsoft.com/en-us/help/13443/windows-which-version-am-i-running).

Due to the fact that Docker is not available for Windows 10 Home, some workarounds are required and will be solved by following this guide.

**Step 1.**

[Download Docker](https://download.docker.com/win/stable/40693/Docker%20Desktop%20Installer.exe) but do not install yet.   
_\(What is_ [_Docker_](https://docs.docker.com/docker-for-windows/install/)_?\)_

Install [Hyper-V](https://www.deskmodder.de/blog/wp-content/uploads/2018/08/hyper-v-installer-1.zip) by running the **.bat** file.  
\([_source_](https://www.deskmodder.de/blog/2018/08/23/windows-10-home-hyper-v-aktivieren/)_\)_

[Virtualization](https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization-must-be-enabled) has to be enabled, which can be checked in the Taskmanager.

![virtualization](https://user-images.githubusercontent.com/26490734/79853838-dba5de80-83c8-11ea-9fbf-d640c4bb1980.png)

**Step 2.**

**Pretend being a Windows10 Pro user**

Open the "Registry Editor" and go to the following path:

`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion`

**change** `EditionID` to `Professional` and `ProductName` to `Windows 10 Pro`

**immediately** open the downloaded Docker File and **install Docker**.

![registryEditor](https://user-images.githubusercontent.com/26490734/80191362-dbe6e980-8615-11ea-9633-3de4909a997d.png)

{% hint style="info" %}
In case of a **PC restart, shutdown or Docker shutdown**, the registry change above needs to be re-entered otherwise Docker will not start.
{% endhint %}

**Step 3.**

Change Docker File sharing settings and create a folder named **"prysm"** in that specific directory.   
In this case the "prysm"-folder has been created in C:\prysm.  


![dockerWindows](https://user-images.githubusercontent.com/26490734/79551080-7c2e9280-8099-11ea-8886-0b739b7d12c1.png)

**Step.4**

Change Docker's default memory to 4GB.

![dockerMemory](https://user-images.githubusercontent.com/26490734/80192514-9aefd480-8617-11ea-93b4-e709a988a5c0.png)

