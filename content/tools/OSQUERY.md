---
title: OSQUERY
summary: "An SQL powered operating system instrumentation, monitoring, and analytics."
description: "An SQL powered operating system instrumentation, monitoring, and analytics."
---

**[https://github.com/osquery/osquery](https://github.com/osquery/osquery)**

## OSQUERY Basis



## OSQUERY Tables Examples


 > 
 > **<font color=red>.tables processes</font>**</br>
 > Processes table.
 > 
 > **<font color=red>SELECT * FROM kernel_info;</font>**</br>
 > Kernel Info table.
 > 
 > **<font color=red>SELECT * FROM shell_history;</font>**</br>
 > Shell history table.

## OSQUERY Query Examples (SQL like)


 > 
 > **<font color=red>SELECT</font> * <font color=red>FROM processes;</font>**</br>
 > 
 > **<font color=red>SELECT</font> pid, name, path <font color=red>FROM processes;</font>**</br>
 > 
 > **<font color=red>SELECT count(</font>\*<font color=red>) from processes;</font>**</br>
 > 
 > **<font color=red>SELECT</font> pid, name, path <font color=red>FROM processes WHERE</font> name='lsass.exe'<font color=red>;</font>**</br>

## OSQUERY WHERE Operators & Wildcards


 > 
 > **<font color=red>=</font>**</br>
 > Equal.
 > 
 > **<font color=red>\<></font>**</br>
 > Not Equal.
 > 
 > **<font color=red>\></font>**</br>
 > Greater than.
 > 
 > **<font color=red>\>=</font>**</br>
 > Greater than or equal to.
 > 
 > **<font color=red>\<</font>**</br>
 > Less than.
 > 
 > **<font color=red>\<=</font>**</br>
 > Less than or equal to.

 > 
 > **<font color=red>BETWEEN</font>**</br>
 > Between a range.
 > 
 > **<font color=red>LIKE</font>**</br>
 > Pattern wildcard searches.
 > 
 > **<font color=red>%</font>**</br>
 > Multiple characters wildcard.
 > 
 > **<font color=red>\_</font>**</br>
 > One character wildcard.

**![](https://lh6.googleusercontent.com/vP_tjGvX4curEEZCc0WBegW-yrGb2b9W-OqUzPJ3s4x_4UXit3wetN4rfhNz6pQpZGLBhur7vzqs5ALuWj1uTmx8eiLn5KdL5Of9um0zcLbhfF3Loiu1BovSj92yYcTbgpAI7JUgh8yNhmChEaIDLw)**

## OSQUERY With YARA

[https://osquery.readthedocs.io/en/stable/deployment/yara/](https://osquery.readthedocs.io/en/stable/deployment/yara/) 

 > 
 > **<font color=red>SELECT * FROM yara WHERE path LIKE '</font>/home/%%<font color=red>' AND sigfile='/var/osquery/yara/scanner.yara';</font>**</br>
 > Execute Yara scan on all files returned by Osquery.

![](https://lh6.googleusercontent.com/D6ak31cKFRP0HZbK2TxO-iYRQozyZxW1hatqFB8s3MUiPjhrzi8D7tBTBS9zfpBdNIM9XRWH9FmqPOfg-McSLmk6Ty7hjUHaq8zSdo9JcVbCG9K05AK8OSgl03DbGYa9nkggQ_cU6Tput4n-wtqsfg)
