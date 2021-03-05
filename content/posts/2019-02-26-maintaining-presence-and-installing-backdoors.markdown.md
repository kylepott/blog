---
author: kylepott
date: 2019-02-26 20:26:38+00:00
draft: false
title: Maintaining Presence and Installing Backdoors
type: post
url: /2019/02/26/maintaining-presence-and-installing-backdoors/
tags:
- armitage
- kali
- metasploit
- msf2
- msfvenom
- PHP
---




By completing this exercise I learned that the best backdoor is one that you don't need to install yourself!  There are two backdoors that I opened up within the Metasploitable 2 operating system (msf2).







The most powerful and easiest backdoor was to login using the root shell, create a new superuser, and then add this user into the SSH list so that I could make use of the existing SSH server configuration.  _Easy-peasy._







I also wanted to install a second backdoor in the event the SSH server was turned off, my new user was spotted and removed, or one of the other root shell access points was patched.  Keep in mind, all the work I've done, to this point, I still do not know the root password.







In brief, I created and uploaded a bind_php shell payload.  I connected with a root shell, logged into the Apache server, uploaded the compromised payload which looks just like a regular PHP file, installed a listener on my attacker machine and then wired together the PHP exploit and the listener.  I consider this attack to be beyond basic and maybe moving into the intermediate category.  Let's break it down.







## Payload







I used MSF Venom to create a compromised PHP file.  I then uploaded and buried this file within the Apache directory.  





![](https://technicalagain.com/wp-content/uploads/2019/02/Screenshot-from-2019-02-25-16-05-26.png)






## Listener







After uploading the compromised PHP file, I configured Armitage to listen to port 4001 at the target machine.







  






![](https://technicalagain.com/wp-content/uploads/2019/02/Screenshot-from-2019-02-25-16-15-03.png)






Once Armitage was listening, all I had to do was navigate to the infected PHP file in any browser and it would connect to the listener automatically.  I now have persistent access to the host in a much more stealthy way.







## Advantages







The PHP backdoor is difficult to identify.  Unless the user is monitoring their own traffic on port 4001, it is unlikely they will spot the file hidden within hundreds of PHP files.







Also, the backdoor only connects and runs when I fire it up remotely, so it is less likely to be spotted.







This technique uses the existing _www-data_ daemon within Apache.  It doesn't require access to any of the users within the operating system.  This is useful in the event that SSH access is closed or my new superuser is discovered and deleted.  I can log in when I need to, browse around the file tree, upload additional compromised files if needed, and download the /etc/passwd file and use John the Ripper to try to gain access to one of the existing accounts.







_Update: I subsequently did crack a few of the other operating system accounts using John.  I have previously written about [my experience with John](https://technicalagain.com/2018/04/17/password-cracking-with-john-the-ripper/) so I tried to avoid using the same techniques in this lab._







## Challenges and Learnings







This was a fun exercise and much more challenging for me.  I feel very proud about this work and feel I'm beginning to move beyond basic techniques into more advanced approaches.







I learned several important lessons.







1.) Having root shell access is much more powerful than gaining shell access through one of the lower privileged daemons.  The daemons are plenty useful, nonetheless.







2.)  I struggled mightily in crafting the right payload, getting the permissions correct to run it, and then connecting up the listener.  I was getting an Access Denied error on the payload until I changed ownership to the _www-data_ service.  I am sure someone more skilled than me would have found a way for Apache to run the payload as root maintaining superuser access in the shell.  I guess I compromised for a little less here.







3.) It would be good for me to create a username/password scheme because the PHP backdoor would be discoverable and usable to other attackers that are scanning the web files.







4.) The PHP backdoor is really easy to remove if spotted.  All the user needs to do is delete the file.  So in a way, while it is well hidden, it is brittle and speaks to all the more reason to install redundant backdoors.  
  








## Conclusion







Over the past two months I compromised the host, exfiltrated data, and installed multiple backdoors to maintain presence.  At this point, I'm now going to turn my attention higher in the stack and start working more diligently on web vulnerability scanning through OpenVAS, Vega, Burp Suite, and other man-in-the-middle proxies.  




