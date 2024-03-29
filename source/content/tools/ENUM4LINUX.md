---
title: ENUM4LINUX
summary: A Linux alternative to enum.exe for enumerating data from Windows and Samba hosts.
description: A Linux alternative to enum.exe for enumerating data from Windows and Samba hosts.
---

**[https://github.com/CiscoCXSecurity/enum4linux](https://github.com/CiscoCXSecurity/enum4linux)**

## Basis


 > 
 > **<font color=red>enum4linux</font> \[TARGET_DOMAIN\]**</br>
 > Linux scan.
 > 
 > **<font color=red>enum4linux -U</font> \[TARGET_DOMAIN\]**</br>
 > Linux Users.

## SMB


 > 
 > **<font color=red>enum4linux -S</font> \[TARGET_DOMAIN\]</br>**
 > List Samba Share.

## Flags


 > 
 > **<font color=red>-U</font>**</br>
 > Get userlist.
 > 
 > **<font color=red>-M</font>**</br>
 > Get machine list.
 > 
 > **<font color=red>-N</font>**</br>
 > Get namelist dump (different from -U and-M).
 > 
 > **<font color=red>-S</font>**</br>
 > Get sharelist.
 > 
 > **<font color=red>-P</font>**</br>
 > Get password policy information.
 > 
 > **<font color=red>-G</font>**</br>
 > Get group and member list.

 > 
 > **<font color=red>-A</font>**</br>
 > All of the above (full basic enumeration).
