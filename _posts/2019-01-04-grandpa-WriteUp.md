---
layout: default
title:  "HTB Grandpa Box Write-Up"
date:   2019-01-04
categories: jekyll update post writeup htb
---

# Grandpa Box Write-Up
### Author: Luke DuCharme (@_nTr0py)
### Date Completed: 04 January 2019
### Difficulty: Easy
### IP: 10.10.10.14
### OS: Windows

### Enumberation Using Nmap:
![nmap screenshot](/img/grandpa/nmap.png)
See Lame write up for description of flags.

* Port 80 is open, and a service enumeration indicates Microsoft IIS httpd 6.0 is running on that port.

### Exploitation
![exploit search](/img/grandpa/exploit_search.png)
* A search in the exploit database shows a few suitable exploits for IIS 6.0. 
* After a series of trial and error, the iis_webdav_scstoragepathfromurl is the best candidate.

![exploit prep](/img/grandpa/exploit_prep.png)
* After setting the remote host to the target as well as changing the default local port for the TCP handler (opsec purposes), the exploit is ready to be run. 

### SA and Privelege Escalation (Privesc)
![exploit 1](/img/grandpa/exploit1.png)
![exploit 2](/img/grandpa/exploit2.png)
* The exploit is successful and a Meterpreter session is spawned. After doing some situational awareness (SA), it's apparent the session is at the user level. Thus, a privesc exploit is required. 
* To determine which one to use, Meterpreter has a script called local_exploit_suggester.

![migration](/img/grandpa/migration.png)
* Before running the script, the Meterpreter session needs to be migrated to a more stable session at the current privelege level. From the process list in the SA, davcdata.exe (PID 2332) seems to be the best option. 
* After a successful migration and running local_exploit_suggester, there are a few possible options, and after trying them, ms14_070_tcpip_ioctl is the best option. 

![privesc](/img/grandpa/privesc.png)
* After backgrounding the session and setting the exploit options, the exploit is successful, and the session's priveleges have been escalated to SYSTEM (woooot woooot 🥳🥳🥳)

### Datamining
* Datamine for the user and administrator flags. (Desktops are normally a good place to look on windows...) 
