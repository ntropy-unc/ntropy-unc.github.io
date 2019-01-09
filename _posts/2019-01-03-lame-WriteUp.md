---
layout: default
title:  "HTB Lame Box Write-Up"
date:   2019-01-03 
categories: jekyll update post writeup htb
---

# Lame Box Write-Up
# Author: Luke Ducharme (@_nTr0py)
### Date Completed: 03 January 2019
### Difficulty: Easy
### IP: 10.10.10.3
### OS: UNIX

### Enumeration Using Nmap:
![nmap screenshot](/img/lame/nmap.png)
* Flags:
  * -T4 : Aggressive (4) speed scans; assumes a fast and reliable network.
  * -A : Aggressive scan. Enables OS detection, version detection, script scanning, and traceroute.
  * -v : Verbose output.
  * -Pn : disables host discovery.

* After looking at the scan results, one sees it is a Unix box running Samba 3.0.20-Debian. 

### Exploitation:
![metasploit exploit search](/img/lame/exploit_search.png)
* After opening the Metasploit Framework, conduct a search using the above command specifying the exploit type and samba.
* Looking at the multi category (unix) for excellent ranked exploits, we see the usermap_script exploit.

![use exploit](/img/lame/exploit.png)
* Use the selected exploit.
* Set rhost to 10.10.10.3 target.
* Run exploit. 

Do a lil dance! 😎😎😎

### Data Mining:
* Search root and user directories for flags. 
