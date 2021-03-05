---
author: kylepott
date: 2018-05-12 02:23:42+00:00
draft: false
title: Scan Wordpress for Vulnerabilities with WPScan
type: post
url: /2018/05/12/scan-wordpress-for-vulnerabilities-with-wpscan/
categories:
- Vulnerability Scanning
- WordPress
- WPScan
---

![](https://technicalagain.com/wp-content/uploads/2018/05/Screenshot-20180511211912-743x667.png)


I scanned my own Wordpress sites for vulnerabilites using a powerful command-line utility, WPScan. WPScan is a black box vulnerability scanner specifically for WordPress. It is a stark reminder why it is so important to minimize the number of plugins you use, delete the ones you have deactivated, and make sure you are keeping your software up-to-date. One simple little command: `sudo wpscan example.com -u` will list all the WordPress usernames, plugins installed, whether active or not, as well as all published vulnerabilities for the plugins, whether they have been fixed, as well as how to exploit them.

WPScan also peeks at the robots.txt file to discover "interesting" content that the author wants hidden from search engines. I made this mistake when I wrote about [rolling my own password manager](https://technicalagain.com/2018/04/05/rolling-my-own-password-manager-part-2/).  Errantly thinking that it would be a good idea to list the directories I don't want indexed in the _robots.txt_ file, I have since deleted this content.

I used WPScan to search for TimThumb (tt) files and used WPScan to brute force password attempts against the usernames I discovered when enumerating the site.


<blockquote>**TimThumb** is a tool used by WordPress themes and plugins to resize images. Old versions of **TimThumb** have a security vulnerability that lets attackers upload malicious ("bad") **files** from another website. The first bad **file** then lets the attacker upload more malicious **files** to the hosting account.</blockquote>


Great utility, powerful, and simple to use.


# Next Steps


It would be a good idea to install a WordPress plugin that forces users to use sufficiently complex passwords and blacklists IP addresses after a certain number of failed login attempts--essentially nullifying the efficacy of bruteforce attacks.

It would also be a good idea to install the Tor proxy so the web host cannot block the IP using WPScan--just a simple technique to hide footprints.
