---
title: POWERVIEW
summary: A PowerShell tool to gain network situational awareness on Windows domains.
description: A PowerShell tool to gain network situational awareness on Windows domains.
---

**[https://github.com/PowerShellMafia/PowerSploit/tree/master/Recon](https://github.com/PowerShellMafia/PowerSploit/tree/master/Recon)**

## Resource

* **[https://book.hacktricks.xyz/windows-hardening/basic-powershell-for-pentesters/powerview](https://book.hacktricks.xyz/windows-hardening/basic-powershell-for-pentesters/powerview)**
* **[https://gist.github.com/HarmJ0y/184f9822b195c52dd50c379ed3117993](https://gist.github.com/HarmJ0y/184f9822b195c52dd50c379ed3117993)**

## POWERVIEW Start


 > 
 > **<font color=red>powershell.exe -ExecutionPolicy bypass</font>**</br>
 > Bypass PowerShell execution policy to run scripts.
 > 
 > **<font color=red>. .\PowerView.ps1</font>**</br>
 > Run POWERVIEW script.

## POWERVIEW Users and Groups


 > 
 > **<font color=red>Get-NetUser</font>**</br>
 > Enumerate users and their properties. 
 > 
 > **<font color=red>Get-NetUser | select cn</font>**</br>
 > Enumerate domain Common Names for users.
 > 
 > **<font color=red>Get-NetUser | select description</font>**</br>
 > Enumeration description for users.

 > 
 > **<font color=red>Get-UserPropery -Properties logoncount</font>**</br>
 > Show connection count (might see a honeypot account).

 > 
 > **<font color=red>Get-NetGroupMember -name "Domain Admins"</font>**</br>
 > Enumerate users belonging to admin groups.
 > 
 > **<font color=red>Get-NetGroup -name \*admin\*</font>**</br>
 > Enumerate all groups with admin in it.

## POWERVIEW Domain


 > 
 > **<font color=red>Get-NetDomain</font>**</br>
 > Infos about the domain.
 > 
 > **<font color=red>Get-NetDomainController</font>**</br>
 > Info about the Domain Controller.

 > 
 > **<font color=red>Get-NetComputer</font>**</br>
 > Infos about servers and computers in the domain.

 > 
 > **<font color=red>Get-DomainPolicy</font>**</br>
 > Infos about Domain Policy.

 > 
 > **<font color=red>Get-NetGPO</font>**</br>
 > List GPOs.
 > 
 > **<font color=red>Get-NetGPO | select displayname, whenchanged</font>**</br>
 > List policies with when they were changed.
