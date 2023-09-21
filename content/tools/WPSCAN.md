---
title: WPSCAN
summary: A WordPress security scanner.
description: A WordPress security scanner.
---

**[https://github.com/wpscanteam/wpscan](https://github.com/wpscanteam/wpscan)**

## Basis


 > 
 > **<font color=red>wpscan --url</font> \[TARGET_IP\] <font color=red>-e u,vp,vt</font>**</br>
 > Scan Wordpress.

## Flags


 > 
 > **<font color=red>-e vp</font>**</br>
 > Enumerate Vulnerable Plugins.
 > 
 > **<font color=red>-e vt</font>**</br>
 > Enumerate Vulnerable Themes.
 > 
 > **<font color=red>-e cb</font>**</br>
 > Enumerate Config Backups.
 > 
 > **<font color=red>-e dbe</font>**</br>
 > Enumerate DB Exports.
 > 
 > **<font color=red>-e u</font>**</br>
 > Enumerate Users.

## WPSCAN WordPress Login Brute Force


 > 
 > **<font color=red>wpscan --url </font>http://\[TARGET_IP\]/blog <font color=red>--usernames</font> admin <font color=red>--passwords</font> <font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Brute force WordPress user's credentials.
