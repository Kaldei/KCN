---
title: MIMIKATZ
summary: "A tool to play with Windows security, written in C."
description: "A tool to play with Windows security, written in C."
---

[https://github.com/gentilkiwi/mimikatz](https://github.com/gentilkiwi/mimikatz)

## MIMIKATZ Base


 > 
 > **<font color=red>load kiwi</font>**</br>
 > Starts Mimikatz.

 > 
 > **<font color=red>help kiwi</font>**</br>
 > Show Mimikatz commands.

 > 
 > **<font color=red>privilege::debug</font>**</br>
 > Ensure this outputs \[output '20' OK\]. Debug allows us to debug a process we normally couldn't access to (administrator privileges).

## MIMIKATZ Enumeration


 > 
 > **<font color=red>systeminfo</font>**</br>
 > Display system infos.
 > 
 > **<font color=red>ipconfig</font>**</br>
 > Display infos about network interfaces.

 > 
 > **<font color=red>getuid</font>**</br>
 > User infos.
 > 
 > **<font color=red>getprivs</font>**</br>
 > Display current user privileges. 

## MIMIKATZ File Upload


 > 
 > **<font color=red>upload</font> myFile**</br>
 > Transfer file to target.

## MIMIKATZ Spawn Shell


 > 
 > **<font color=red>shell</font>**</br>
 > Open a shell.
