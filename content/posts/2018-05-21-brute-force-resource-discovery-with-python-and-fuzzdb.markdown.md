---
author: kylepott
date: 2018-05-21 01:05:40+00:00
draft: false
title: Brute Force Resource Discovery with Python and FuzzDB
type: post
url: /2018/05/21/brute-force-resource-discovery-with-python-and-fuzzdb/
categories:
- brute
- forzabruta
- Resource Discovery
---

![](https://technicalagain.com/wp-content/uploads/2018/05/Screenshot-20180520133922-782x462.png)


I have been working through a Python course on [Lynda.com](https://www.lynda.com/Python-tutorials/Building-our-first-brute-forcer/521198/532917-4.html) and in the course we wrote a brute force resource discovery tool using Python.  You put in a URL and then you specify a dictionary word list, and the number of threads to run concurrently.  Then the brute forcer, named ForzaBruta.py, works through the word list and gives the page response codes (404, 403, 200, etc.).

I used the FuzzDB [predictable filepaths](https://github.com/fuzzdb-project/fuzzdb/blob/master/discovery/predictable-filepaths/filename-dirname-bruteforce/raft-large-directories-lowercase.txt), file and directory name brute forcer, Raft large directories lowercase dictionary list. I ran this on my main URL in hopes of seeing if I could discover the password manager I described [twice](https://technicalagain.com/2018/03/31/rolling-my-own-proper-password-manager/) [previously](https://technicalagain.com/2018/04/05/rolling-my-own-password-manager-part-2/). To my dismay, I was able to find the password manager within 15 minutes. I then narrowed the URL and re-ran ForzaBruta again. Bang, my password manager was discovered within 45 minutes. Mind you, the password manager was discovered without a single link going to the actual application and I did not have noteworthy entries in the robots.txt file.

This is a handy utility!


## Learnings


1. First of all, remember that nothing truly hides in plain site on the Internet.

2. I should have picked directory structure names that were random and un-guessable via a brute force dictionary attack. I now have to make this update.

3.  My web host did not detect this attack and has no controls in place to prevent it.  Also the analytics I run on the site are delayed and they also do not do an adequate job recording the 404 end points - no help there.  While it would be pretty easy to create a honeypot to spot a brute force attack, none of the controls I have in place spotted this one.
