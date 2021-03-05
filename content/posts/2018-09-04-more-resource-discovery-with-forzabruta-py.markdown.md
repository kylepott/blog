---
author: kylepott
date: 2018-09-04 18:27:07+00:00
draft: false
title: More Resource Discovery with ForzaBruta.py
type: post
url: /2018/09/04/more-resource-discovery-with-forzabruta-py/
categories:
- brute
- forzabruta
- Kali
- Linux
- Projects
- ProjectSuccess
- Resource Discovery
---

![](https://technicalagain.com/wp-content/uploads/2018/09/Screenshot-20180904113500-960x204.png)


Been a busy summer, but I spent some time continuing the work [I previously wrote about the brute-forcer, ForzaBruta.py.](https://technicalagain.com/2018/05/21/brute-force-resource-discovery-with-python-and-fuzzdb/)  This time working through the Lynda coursework to iterate on the brute-forcer to add convenience and analysis capabilities:



 	  * Take screenshots
 	  * Capture the MD5 checksum to compare the file contents
 	  * Record number of words and characters in each file and the time to load
 	  * Filtering and coloring based on return code
 	  * Filter for only certain file extensions.

These new capabilities rely on [Selenium](https://www.seleniumhq.org/), a browser automation utility, and [PhantomJS](http://phantomjs.org/), a scriptable headless browser.  The convenience features are nice.  I have not been able to get automated screenshots to work.  All seemingly works well except a zero byte PNG file is created.  I am assuming the issue is related to the nuance of having Kali installed on a MacBook.  These graphics challenges are difficult to debug.  I experienced a similar graphics issue working with Hashcat last month as well.

That's a long way for me to say I don't think I'm going to invest the time to get the screenshot capabilities working.
