---
author: kylepott
date: 2018-04-22 21:26:37+00:00
draft: false
title: More Password Cracking - Windows Edition with Ophcrack
type: post
url: /2018/04/22/more-password-cracking-windows-edition-with-ophcrack/
categories:
- Cracking
- Ophcrack
- Password
- Projects
---

I continued the work I [previously explained](https://technicalagain.com/2018/04/17/password-cracking-with-john-the-ripper/) by attempting to crack a Windows administrator password. This time I created a new windows administrator, booted up using a Kali Linux USB and launched Ophcrack to go after the administrator account I set up.

After lauching Ophcrack, I navigated to the Windows partition and then \WINDOWS\System32\Config to access the SAM database.  I then downloaded a Rainbow Table called Vista Free and after about 10 minutes, the admittedly weak password I setup _hello123 _was cracked_.  _I was not able to crack all of the accounts - presumably because they were adequately complex![](https://technicalagain.com/wp-content/uploads/2018/04/0-1024x498.jpeg)
.

I think next time I will experiment with _chntpw_ to reset the Administrator password instead of attempting to crack it.


