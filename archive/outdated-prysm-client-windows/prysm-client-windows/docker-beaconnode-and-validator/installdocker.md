# Installing Docker on Windows Home

#### **Installing Docker on Windows Home**

**Step 0.**

Make sure you have [Windows10 Home](https://support.microsoft.com/en-us/help/13443/windows-which-version-am-i-running).

Since Docker is not available for Windows 10 Home, some workarounds are required and are solved by following this guide.

**Step 1.**

[Download Docker](https://download.docker.com/win/stable/40693/Docker%20Desktop%20Installer.exe) but do not install yet.&#x20;

Install [Hyper-V](https://www.deskmodder.de/blog/wp-content/uploads/2018/08/hyper-v-installer-1.zip) by running the **.bat** file. ([_source_](https://www.deskmodder.de/blog/2018/08/23/windows-10-home-hyper-v-aktivieren/)_)_

[Virtualization](https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization-must-be-enabled) must be enabled ([Guide](https://support.bluestacks.com/hc/en-us/articles/115003174386-How-can-I-enable-virtualization-VT-on-my-PC-))

![virtualization](https://user-images.githubusercontent.com/26490734/79853838-dba5de80-83c8-11ea-9fbf-d640c4bb1980.png)

**Step 2.**

**Pretend being a Windows10 Pro user**

1.  Open the "Registry Editor" and go to the following path:

    `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion`\
    ****
2. **Change** `EditionID` to `Professional` and `ProductName` to `Windows 10 Pro`\

3. **Immediately** open the downloaded Docker File and **install Docker**.

![registryEditor](https://user-images.githubusercontent.com/26490734/80191362-dbe6e980-8615-11ea-9633-3de4909a997d.png)

{% hint style="info" %}
In case of a **PC restart, shutdown or Docker shutdown**, the registry change above needs to be re-entered otherwise Docker will not start.
{% endhint %}

**Step 3.**

Change Docker File sharing settings and create a folder named **"prysm"** in that specific directory. \
In this case the "prysm"-folder has been created in C:\prysm.\


![dockerWindows](https://user-images.githubusercontent.com/26490734/79551080-7c2e9280-8099-11ea-8886-0b739b7d12c1.png)

**Step.4**

Change Docker's default memory to 4GB.

![dockerMemory](https://user-images.githubusercontent.com/26490734/80192514-9aefd480-8617-11ea-93b4-e709a988a5c0.png)
