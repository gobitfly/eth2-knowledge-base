# Run with Windows using binary files \(.exe\)

#### Windows 10 w/Binary files \(.exe\) 

{% hint style="info" %}
#### Validator client currently not working - requires a [fix](https://github.com/prysmaticlabs/prysm/issues/5456#issue-601128068) by PrysmaticLabs
{% endhint %}

**Step 0.**

Open the [Prysmatic Participation Page](https://prylabs.net/participate) and the [client release page](https://github.com/prysmaticlabs/prysm/releases)**.**

**Step 1.**

Open a [Command Prompt](https://www.wikihow.com/Open-the-Command-Prompt-in-Windows) window and enter the following: 

`reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1`

{% hint style="info" %}
 **This is not required. Just a cosmetic fix to your command prompt output.**
{% endhint %}

**Step 2.**

**Download** the newest versions of the beaconchain **and** validator clients. The version name might have changed because of an update, but the file name should similar \(green mark on the picture below\).

![Prysmatic\_DownloadPage](https://user-images.githubusercontent.com/26490734/79451678-33b69c80-7fe7-11ea-80c8-b92c75fbb937.png)

**Step 3.**

Find the files that have been downloaded. Usually located in the "Downloads" folder

**Step 4.**

Open the beaconchain file  "**beacon-chain**-v1.0.0-alpha.2-windows-amd64.exe".   
A **warnining** should appear. **Click** on "More Info" and then "Run anyway".

![Prysmatic\_DownloadWarning](https://user-images.githubusercontent.com/26490734/79451935-a1fb5f00-7fe7-11ea-875d-f443afe24b09.png)

1. **If this does not work**, you can also open a "Command Prompt" window and drag&drop the beaconchain file into it and press enter.
2. **If you get the error** `The process cannot access the file because it is being used by another process`,  you will need **manually** delete the "beaconchain.db" file.

\*\*\*\*

**Windows 10 w/Binary files \(.exe\) - Validator** \(REQUIRES [A FIX BY PRYSM TEAM](https://github.com/prysmaticlabs/prysm/issues/5456#issue-601128068)**\)**

