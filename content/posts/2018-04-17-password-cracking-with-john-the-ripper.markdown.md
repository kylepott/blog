---
author: kylepott
date: 2018-04-17 02:11:59+00:00
draft: false
title: Password Cracking with John the Ripper
type: post
url: /2018/04/17/password-cracking-with-john-the-ripper/
categories:
- Cracking
- John
- Password
---

I did some preliminary experimenting with password cracking utility John the Ripper to test the security of my own root password.  I started by installing John and  dumping the _/etc/passwd_ file.

`sudo apt-get install john`

`unshadow /etc/passwd /etc/shadow > mypasswd.txt`

The _mypasswd.txt_ file now holds a salted hash of my root password.  I then passed this over to John to work its magic.

`john mypasswd.txt`

John is very powerful.  I experimented with the most basic of cracking settings starting with single mode, then word lists and John would have moved to an incremental mode.  I am happy to say I chose a sufficiently complex password that withstood John's single crack mode and word lists.

Password cracking is very CPU intensive and the 10+ year old server that I am working with is probably about the least appropriate computer to attempt a rigorous cracking approach.  The fan kicked on immediately and my laptop starting running hot.  After more than 10 minutes of cracking attempts I aborted John and you can see the output below.

![](https://technicalagain.com/wp-content/uploads/2018/04/Screenshot-from-2018-04-16-21-04-37.png)


This was a fun and great learning exercise.  I am going to continue experimenting with John. I will test John on the passwords stored in my [Password Manager](https://technicalagain.com/2018/04/05/rolling-my-own-password-manager-part-2/) next.  [Using this technique](https://prakharprasad.com/windows-password-cracking-using-john-the-ripper/) I will also mount the Windows partition I have on my server and attempt to access and crack the Windows password hashes from Ubuntu.
