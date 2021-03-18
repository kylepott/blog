---
author: kylepott
date: 2017-11-07 01:58:27+00:00
draft: false
title: We landed here, on the internet, safely in one piece!
type: post
url: /hello-world/
categories:
- cPanel
- FileZilla
- FTP
- MySQL
- Projects
- ProjectSuccess
- WordPress
---

Our first project is in the can!  I call this project "Make a Website, Start Following Through on Your Development Plan."

The first step was to find a domain name using [Instant Domain Search](http://instantdomainsearch.com).  I've been using this site for at least 5 years and it remains the fastest and simplest way to find a domain.

I then bought the cheapest hosting plan on [Bluehost](http://www.bluehost.com) after hearing an advertisement on The Bill Simmons podcast.  Like Instant Domain Search, I have at least 5 years of experience with Bluehost.  I wanted a hosting plan that was basic, but would let me fully manage and run my own server including giving me the ability to experiment with a variety of programming languages and databases.  I bought the bear minimum services, opting for just a domain name, some basic hosting, and for 99 cents a whois proxy to keep my personal information safe.

The next step was to delete the default WordPress installation that Bluehost sets up, because of [Rule #1: We prefer to build our own ](http://technicalagain.com/what-are-we-doing-here/ground-rules/)and then I uploaded my own version of [WordPress](http://wordpress.org).  I used cPanel to builtd a new database for the WordPress install.  For some reason, the user privileges on the default MySQL database on Bluehost were not working.  So I created a new database then created a new database user, linked the two together, and completed the World Famous 5 Minute WordPress install.

After some customizing and minimal-izing, here we are.  Along the way I had an impossible time getting the FTP Client to work on my Chromebook so I upgraded my Chromebook to Ubuntu (more on that in a few days).  I also introduced some horrible password and identity management behavior by reusing a subset of the same username and password combination to try to work fast, a violation of [Rule #4](http://technicalagain.com/what-are-we-doing-here/ground-rules/).  I plan to clean that up in a future post when I explore using a password manager.

According to [Rule #2: we always beep our costs low](http://technicalagain.com/what-are-we-doing-here/ground-rules/).  I fared quite well in this area walking away with a year's worth of this website for $71.28.

On to project number two in a few days: detailing how I installed Ubuntu Linux on my Acer Chromebook.
