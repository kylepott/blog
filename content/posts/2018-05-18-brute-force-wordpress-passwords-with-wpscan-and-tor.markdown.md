---
author: kylepott
date: 2018-05-18 00:54:54+00:00
draft: false
title: Brute Force WordPress Passwords with WPScan and Tor
type: post
url: /2018/05/18/brute-force-wordpress-passwords-with-wpscan-and-tor/
categories:
- Cracking
- Password
- WordPress
- WPScan
---

![](https://technicalagain.com/wp-content/uploads/2018/05/Screenshot-20180517195011-785x463.png)

Visit [Center City Security](https://centercitysecurity.com?utm_source=TechnicalAgain.com&utm_medium=https://technicalagain.com/2018/05/18/brute-force-wordpress-passwords-with-wpscan-and-tor/&utm_campaign=Technical Again Brute Force Wordpress Passwords with wpscan and tor&utm_content=header) for WordPress Penetration Testing and Security services.

I took another crack, pun intended, at brute forcing my WordPress password using WPScan. Unlike when I tried [it the other day](https://technicalagain.com/2018/05/12/scan-wordpress-for-vulnerabilities-with-wpscan/), this time I used Tor and set up a SOCKs proxy to make use of a false IP address. My thinking was that my web host might black list my IP after a certain number of failed attempts, so by using Tor I could simply switch IP addresses once the blacklist went into effect.

I am happy to say the proxy worked and the following command worked as expected:

`sudo wpscan --url technicalagain.com --wordlist darkc0de.txt --username [redacted] --proxy socks5://127.0.0.1:9050 -v `

The behavior of my web host did not match what I expected. Instead of blacklisting the IP, as soon as the 38th incorrect password was entered, the web host put up a 406 error and stopped allowing log in attempts for five minutes. Why does it allow 38 password attempts? Good question. So, to work around this I would have to enter 37 passwords, then wait five minutes, then enter the next 37 passwords, then wait five minutes, and slowly work through the entire dictionary list. At 37 passwords per five minutes it would take 121 days to exhaust the list of passwords on darkc0de.txt. Suffice it to say that this password policy control in place by the web host is a satisfactory deterrent for 99.99% of attackers that are not going to wait up to half a year just in hopes that my password is on the darkc0de list. It isn't.

Visit [Center City Security](https://centercitysecurity.com?utm_source=TechnicalAgain.com&utm_medium=https://technicalagain.com/2018/05/18/brute-force-wordpress-passwords-with-wpscan-and-tor/&utm_campaign=Technical Again Brute Force Wordpress Passwords with wpscan and tor&utm_content=footer) for WordPress Penetration Testing and Security services.
