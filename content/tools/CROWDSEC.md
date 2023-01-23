---
title: CROWDSEC
summary: An open-source and paticipative IDS and IDS.
description: An open-source and paticipative IDS and IDS.
---

**[https://www.crowdsec.net/](https://www.crowdsec.net/)**

## CROWDSEC Installation


 > 
 > **<font color=orange>curl -s https://packagecloud.io/install/repositories/crowdsec/crowdsec/script.deb.sh | sudo bash</font>**</br>
 > Install CrowdSec Repository.''

 > 
 > **<font color=orange>sudo apt install crowdsec</font>**</br>
 > Install CrowdSec. This only installs the detection part (it's an IDS).

 > 
 > **<font color=orange>sudo apt install crowdsec-firewall-bouncer-iptables</font>**</br>
 > Install the Bouncer. This installs the prevention part (it's now an IPS)

## CROWDSEC Commands


 > 
 > **<font color=red>cscli hub list</font>**</br>
 > Show CrowdSec collections, parsers, scenarios.
 > 
 > **<font color=red>cscli alerts list</font>**</br>
 > Show CrowdSec actions.
 > 
 > **<font color=red>cscli decisions list</font>**</br>
 > Show CrowdSec actions.

 > 
 > **<font color=red>cscli collections install</font> crowdsecurity/apache2**</br>
 > Install a new collection. Collections are available here:  https://hub.crowdsec.net/browse/
 > 
 > **<font color=red>/usr/share/crowdsec/wizard.sh -c</font>**</br>
 > Enable other collections.
