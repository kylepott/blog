---
author: kylepott
date: 2018-05-19 18:39:50+00:00
draft: false
title: Information Gathering with DMitry
type: post
url: /2018/05/19/information-gathering-with-dmitry/
categories:
- DMitry
- Kali
---

DMitry is a nice little utility built into Kali. It's a basic and easy to use utility, but not great. Usage is straight forward.

`dmitry technicalagain.com`





<blockquote>Base functionality is able to gather possible subdomains, email addresses, uptime information, tcp port scan, whois lookups, and more. </blockquote>




DMitry is worth the effort to simply punch in the command line but don't expect great information back. First, just about everyone is using a whois proxy to conceal their personal information. Second, DMitry relies on search engines to try to find subdomains and email addresses. I specifically tested these features and because the search engines missed, DMitry missed, too. Simple and quick to use, but the information that comes back is not that helpful. 
