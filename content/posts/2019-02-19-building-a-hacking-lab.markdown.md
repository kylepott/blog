---
author: kylepott
date: 2019-02-19 00:32:39+00:00
draft: false
title: Building a Hacking Lab
type: post
url: /2019/02/19/building-a-hacking-lab/
tags:
- kali
- msf2
- ubuntu
- virtualbox
---


![](https://technicalagain.com/wp-content/uploads/2019/02/Screenshot-from-2019-02-18-18-21-58.png)






I spent the afternoon yesterday building a local hacking lab.  After installing Ubuntu and VirtualBox, I grabbed a copy of Metasploitable (msf2) as well as a copy of Kali.  msf2 is a version of Ubuntu that intentionally has a number of security vulnerabilities built in to give you a chance to practice your offensive security techniques.







One adjustment I had to make was to tweak the VirtualBox settings to bridge the network connection for msf2 and Kali.  The default setting was NAT and what was happening was the host was sharing the IP with each virtual machine so when I ran an nmap scan from Kali over to msf2 it showed all ports closed.  That's when I realized I was essentially recursively scanning Kali instead of msf2.  Made the adjustment and was good to go!  




