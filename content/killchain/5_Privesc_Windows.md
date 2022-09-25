---
title: 5 – Privesc Windows
summary: Privilege Escalation step – a note for elevating privileges on a Windows machine.
description: Privilege Escalation step – a note for elevating privileges on a Windows machine.
---

# Privesc Checklist

---

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

# Automated Scripts

---

### POWERUP

https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1

 > 
 > **<font color=red>. .\PowerUp.ps1</font>**</br>
 > **<font color=red>Invoke-AllChecks</font>**

---

### EXPLOIT-SUGGESTER

https://github.com/AonCyberLabs/Windows-Exploit-Suggester 

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

https://github.com/carlospolop/PEASS-ng/releases

 > 
 > **<font color=red>winPEASx64.exe</font>**

---

### PRIVESCHECK

https://github.com/itm4n/PrivescCheck

 > 
 > **<font color=red>Set-ExecutionPolicy Bypass -Scope process -Force</font>**</br>
 > **<font color=red>. .\PrivescCheck.ps1</font>**</br>
 > **<font color=red>Invoke-PrivescCheck</font>**</br>
