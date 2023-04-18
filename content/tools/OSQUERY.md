---
title: OSQUERY
summary: "An SQL powered operating system instrumentation, monitoring, and analytics."
description: "An SQL powered operating system instrumentation, monitoring, and analytics."
---

**[https://github.com/osquery/osquery](https://github.com/osquery/osquery)**

## OSQUERY Base


 > 
 > **<font color=red>osquery</font>**</br>
 > Enter Osquery console.

 > 
 > **<font color=red>.help</font>**</br>
 > Show help.
 > 
 > **<font color=red>.version</font>**</br>
 > Show version

 > 
 > **<font color=red>.tables</font>**</br>
 > List all available tables.
 > 
 > **<font color=red>.schema</font> \[TABLE_NAME\]**</br>
 > Display schema of the table.

 > 
 > **<font color=red>.tables</font> \[TABLE_NAME\]**</br>
 > Display table content.

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
