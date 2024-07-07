This is a challenge that is exactly what is says on the tin, there are a few challenges around investigating a windows machine that has been previously compromised.

Connect to the machine using RDP. The credentials the machine are as follows:

Username: Administrator
Password: letmein123!

Please note that this machine does not respond to ping (ICMP) and may take a few minutes to boot up.

Whats the version and year of the windows machine?
Use the following command in Command Prompt to get the version and year of the Windows machine:

systeminfo | findstr /B /C:"OS Name" /C:"OS Version"
This command retrieves the operating system name and version.

```bash
Microsoft Windows [Version 10.0.14393]
(c) 2016 Microsoft Corporation. All rights reserved.

C:\Users\Administrator>systeminfo | findstr /B /C:"OS Name" /C:"OS Version"
OS Name:                   Microsoft Windows Server 2016 Datacenter
OS Version:                10.0.14393 N/A Build 14393

C:\Users\Administrator>
```

also :

```bash
Get-ComputerInfo -Property “Os*”
```


Which user logged in last?

To find out which user logged in last on a Windows machine, use the following command in Command Prompt:

```sh
Windows PowerShell
Copyright (C) 2016 Microsoft Corporation. All rights reserved.

PS C:\Users\Administrator> Get-LocalUser

Name           Enabled Description
----           ------- -----------
Administrator  True    Built-in account for administering the computer/domain
DefaultAccount False   A user account managed by the system.
Guest          True    Built-in account for guest access to the computer/domain
Jenny          True
John           True


PS C:\Users\Administrator>
```


When did John log onto the system last?

Answer format: MM/DD/YYYY H:MM:SS AM/PM

```bash
PS C:\Users\Administrator> net user john |findstr “Last”   Last logon                   3/2/2019 5:48:32 PM           PS C:\Users\Administrator>                                                                                            
```

What IP does the system connect to when it first starts?

How To:
Let us look at the host file to see if the answer can be found in the host file. The file path is, C:\ > Windows > System32 > drivers > etc, once in this folder double-click on the hosts file.