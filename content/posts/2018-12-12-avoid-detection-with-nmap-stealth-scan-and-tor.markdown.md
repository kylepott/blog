---
author: kylepott
date: 2018-12-12 02:06:28+00:00
draft: false
title: Avoid Detection with Nmap Stealth Scan and Tor
type: post
url: /2018/12/12/avoid-detection-with-nmap-stealth-scan-and-tor/
categories:
- Kali
- nmap
- tor
---


![](https://technicalagain.com/wp-content/uploads/2018/12/Screenshot-from-2018-12-11-07-38-46.png)






The nmap stealth scan -sS flag allows you to search for open ports by adjusting the TCP/IP three way handshake:







The handshake ordinarily is SYN -> SYN ACK -> ACK 







The -sS flags change the handshake to SYN -> SYN ACK -> RST







Defined: Synchronize, Acknowledge, Reset







This makes it less likely, but certainty not impossible for an intrusion detection system to pickup the scan.







The best approach that I can think of would be to use the -sS flag and between each port tested use Tor to change IPs from within a regionally anticipated region based on the purpose and location of the target.  There is a great write up on how to do just that [here](https://www.shellhacks.com/anonymous-port-scanning-nmap-tor-proxychains/) using Tor and Proxy Chains to use public proxies.







The article also mentions using the _tor-resolve_ feature to resolve a hostname to an IP address to avoid all of your queries going through the DNS server of the ISP. Nmap allows the -n flag to never use DNS name resolution and the -Pn flag to avoid host discovery.  








That leaves me with the following command after using tor-resolve on technicalagain.com: sudo proxychains nmap -sS -n -PN -v 173.194.34.174







_Update: Also don't forget the -O flag to learn the operating system and hosting service._



