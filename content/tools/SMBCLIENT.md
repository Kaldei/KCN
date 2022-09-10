---
title: SMBCLIENT
---

## SMBCLIENT Base


 > 
 > **<font color=red>smbclient -L </font>\[TARGET_IP\]<font color=red> --no-pass</font></br>**
 > List Shares anonymously.

 > 
 > **<font color=red>smbclient -L </font>\[TARGET_IP\]<font color=red> -U</font> myUser</br>**
 > List Shares with a user.

 > 
 > **<font color=red>smbclient</font> <font color=red>//</font>\[TARGET_IP\]<font color=red>/</font>mySmbShare</br>**
 > Connect to a Share.

## SMBCLIENT Flags


 > 
 > **<font color=red>-L</font></br>**
 > List Shares.
 > 
 > **<font color=red>-U</font> myUser</br>**
 > Specify the user.
 > 
 > **<font color=red>-N</font></br>**
 > No password (--no-pass).
 > 
 > **<font color=red>-p</font> 12</br>**
 > Specify the port.
