---
title: NUCLEI
summary: A fast and customizable vulnerability scanner based on simple YAML DSL.
description: A fast and customizable vulnerability scanner based on simple YAML DSL.
---

**[https://github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei)**

## Installation

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
 > **<font color=red>nuclei -u</font> -list myTagets.txt**</br>
 > Scan all targets in text file with all available templates.
 > 
 > **<font color=red>nuclei -d</font> myFolder  <font color=red>-u</font> \[TARGET_IP\]**</br>
 > Scan target with templates in the specified folder.
