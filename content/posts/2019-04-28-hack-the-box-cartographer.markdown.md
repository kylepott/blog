---
author: kylepott
date: 2019-04-28 02:27:02+00:00
draft: false
title: Hack the Box - Cartographer + Grammar
type: post
url: /2019/04/28/hack-the-box-cartographer/
tags:
- apache
- blns
- cve
- dirb
- hackthebox
- htb
- hydra
- nmap
- ubuntu
---




[Hack the Box](https://www.hackthebox.eu/) is a great free resource to play capture the flag by practicing penetration testing on a variety of different labs spanning just about every domain of offensive security.  Over the past few months I completed two introductory exercises, HDC and Lernaen. 







This weekend I cleared Cartographer _(update: and Grammar - more at the very bottom)_ and will detail my approach and learnings below.  In doing these exercises, so much learning happens figuring out what _doesn't_ work.







### What didn't work?







When you open the lab you're presented with a basic web form.  





![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-27-20-47-29.png)






After doing reconnaissance, I learned and formulated the following plans.





  * The web form gives no error message for incorrect credentials.  _I could automate a high volume credential brute force attack._ The web form is a basic username:password "POST" interaction with the server.  Pretty standard, pretty straightforward.  * I browsed the source code.  Nothing juicy, no JavaScript, no custom approaches to authentication.  * I browsed for _.htaccess, robots.txt. _ No help.  * I could use dirb to enumerate the directory structure and PHP page names.  * I used nmap to fingerprint and learn it is an Ubuntu server running Apache 2.4.18.  The main page is written in PHP.  _I could try some of the excellent [CVEs published](https://www.cvedetails.com/vulnerability-list/vendor_id-45/product_id-66/version_id-199589/Apache-Http-Server-2.4.18.html) due to Apache being unpatched._  * Lastly, if nothing else was successful, I could try SQL injection, server injection and a number of other malformed inputs using the [Big List of Naughty Strings](https://github.com/minimaxir/big-list-of-naughty-strings).





I used Hydra to automate a bruteforce attack on the credentials.  I did this by starting with a list of all of the basic Apache and tomcat default credentials.  This took a long time, but did not help.







I then used dirb and discovered two interesting pages: _/server-status,_ a default Apache page which was hidden behind a 403 forbidden page.  As well as _panel.php_ which was a 300 redirect back to _index.php_. I lost a lot of time using Metasploit and Burpsuite to attempt to hack into these pages using exploits and manipulating the headers.  My thinking was that I might be able to exploit the unpatched version of Apache.  Wrong! This turned out to be a distraction.







Finally, I referenced the Big List of Naughty Strings and manually attempted a number of fuzzing queries including server code injection, URL hacking, XXE injection, file inclusion, and then SQL injection.  Copying and pasting either of these commands into both the username and password fields worked: ' OR 1=1 -- 1 and ' OR '1'='1.  I tried to automate these attacks using Burpsuite, but still have a lot to learn there.





![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-27-21-06-08.png)






### What worked







The SQL injection unlocked two important pieces of information.







1.) The URL changed to /_panel.php?info=home _What else could home be changed to?







2.) A cookie with _PHPSESSID_ was established and used for session management. 







I customized dirb by passing in the cookie with the _PHPSESSID_ and I used the _common.txt_ wordlist and bingo.  I found the flag and completed the exercise.  This took three iterations.  At first dirb gave me no results, because I did not pass the cookie.  Then I used the small.txt wordlist which was too small.  On my third try I finally found the flag.





![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-27-20-26-01.png)






### Reflections...







I didn't prioritize my work well.  I started with some heavy, somewhat advanced and time consuming attacks before I finished reconaissance and thought through my approach.  I bypassed the simpler stuff which ended up being the _effective_ stuff.  I'm going to try to do better than that in the next lab.







Hack the Box is a lot of fun.  Great learning.  A truly awesome resource.  I'm going to try to tackle Grammar next.  Grammar is the toughest web lab on Hack the Box so we'll see. 







_Update: I did end up completing Grammar today, too.  I used many of the same reconnaissance techniques on Grammar and Cartographer.  I won't elaborate much on Grammar, but I will say I did use one hint, I needed syntax help to remove quotes and add in a semi-colon when cookie hijacking._







_Grammar requires a similar approach to actually getting a Hack the Box invite: Change a GET request to a POST request, decode a session cookie, and take advantage of PHP type juggling vulnerability. I learned a lot about Burp in this exercise and a whole lot about PHP type comparisons.    
_



