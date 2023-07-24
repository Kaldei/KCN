---
title: NUCLEI
summary: A fast and customizable vulnerability scanner based on simple YAML DSL.
description: A fast and customizable vulnerability scanner based on simple YAML DSL.
---

**[https://github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei)**

## Install


 > 
 > https://github.com/projectdiscovery/nuclei/releases
 > 
 > **<font color=orange>go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest</font>**</br>

## Basis


 > 
 > **<font color=red>nuclei</font>**</br>
 > Download base templates (install at `~/nuclei-templates`).

 > 
 > **<font color=red>nuclei -u</font> \[TARGET_IP\]**</br>
 > Scan target with all available templates.
 > 
 > **<font color=red>nuclei -u -list</font> myTagets.txt**</br>
 > Scan all targets in text file with all available templates.

## Templates


 > 
 > https://github.com/projectdiscovery/nuclei-templates

 > 
 > **<font color=red>nuclei -u</font> \[TARGET_IP\]  <font color=red>-t</font> myFolder**</br>
 > Scan target with templates in the specified folder.

## Flags


 > 
 > **<font color=red>-rl</font> 30**</br>
 > Set Rate Limit.
 > 
 > **<font color=red>-header</font> 'myHeader:customValue''**</br>
 > Add a header to the request (can be used to inform the admin server that wa are attacking).

 > 
 > **<font color=red>-tags</font> xss**</br>
 > Filter templates by tags.
 > 
 > **<font color=red>-severity</font> low,medium,high,critical**</br>
 > Filter templates by severity.
