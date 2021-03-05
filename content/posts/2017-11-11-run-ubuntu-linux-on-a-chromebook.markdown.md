---
author: kylepott
date: 2017-11-11 01:03:05+00:00
draft: false
title: Run Ubuntu Linux on a Chromebook
type: post
url: /2017/11/11/run-ubuntu-linux-on-a-chromebook/
categories:
- Chromium
- Crouton
- FileZilla
- FTP
- Projects
- ProjectSuccess
- Ubuntu
---

![](https://technicalagain.com/wp-content/uploads/2017/11/a-1024x576.jpg)


Project number 2 is in the can! I am now running Ubuntu Linux on my Acer Chromebook in a dual boot environment thanks to [Crouton](https://github.com/dnschneid/crouton).  Actually, it would be more accurate to say that I am running Ubuntu Linux concurrently and on top of the Chromium kernel. This [11 inch 64 bit Intel white workhorse](https://www.amazon.com/gp/product/B00MMLV7VQ/ref=oh_aui_search_detailpage?ie=UTF8&psc=1) met my needs for casual browsing since I first bought it in April of 2015.  Great battery life, to boot. But, I expect that in taking on this year of development and the many technical projects I have in mind I need more horsepower.  So, in [honoring Rule #2](http://technicalagain.com/what-are-we-doing-here/ground-rules/), rather than buying a new laptop or spending any money, I wanted to breathe new life into hardware I already had. Call it the classical approach to technology.  Since Chromebooks are already written on top of the Linux kernel, it made getting going with Linux pleasantly simple.

I followed [these instructions](https://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/) and was pleased that more than a year later and they still worked without issue.  I chose to install Ubuntu with the Xfce desktop enviornment because it is fast and light on system resources.  It's not much of a looker, but it is powerful.  Once I landed in the desktop I fired up the terminal did a quick

`sudo apt-get install filezilla`

I installed the powerful FileZilla FTP client--much better experience than using sFTP which kept failing in Chrome.  Back in cPanel I created a new FTP user and I finished uploading WordPress.  Back in Ubuntu, I also grabbed Firefox

`sudo apt-get install firefox`

for a better browser experience and then I logged out.  On logout, Ubuntu closes and you're brought right back to the session you left in Chrome.  I am loving having the simplicity of chrome right alongside the power of Ubuntu.  Now whenever I want to launch Linux I hit CRTL+ALT+T to launch the terimnal then:

`shell`
`sudo startxfce4`


### Learnings


This was my first encounter with Crouton and it was a great experience.  Admittedly, I was unfamiliar with chroot.  From the GitHub, here's a nice concise explanation and a quick pro/con analysis.


<blockquote>Like virtualization, chroots provide the guest OS with their own, segregated file system to run in, allowing applications to run in a different binary environment from the host OS. Unlike virtualization, you are _not_ booting a second OS; instead, the guest OS is running using the Chromium OS system. The benefit to this is that there is zero speed penalty since everything is run natively, and you aren't wasting RAM to boot two OSes at the same time. The downside is that you must be running the correct chroot for your hardware, the software must be compatible with Chromium OS's kernel, and machine resources are inextricably tied between the host Chromium OS and the guest OS. What this means is that while the chroot cannot directly access files outside of its view, it _can_ access all of your hardware devices, including the entire contents of memory. A root exploit in your guest OS will essentially have unfettered access to the rest of Chromium OS.</blockquote>


Thanks to [David Schneider](https://github.com/dnschneid) and the other contributors for his generous and amazing work on Crouton.


### Stumbling Blocks


A few things where challenging on this project.  I didn't read the instructions carefully enough the first few times and I had a difficult getting my Chromebook in developer mode.  The Chrome interface for develop mode was pretty intimidating and the bios made some of the scariest beeping sounds I've ever heard.  Besides that this project was pretty straight forward and clean.

I did manage to build more horrible identity management habits by not using a password for my sudo account in Chrome, having a riduculously guessable password in Ubuntu, and then reusing my same user ID and pass for FTP, host,  WordPress, and the WordPress database.  Keeping things easy for the hackers.  Just kidding, we are going to address password management in a future project.

Oh yeah, I also had to fight an acute, but strong desire to just buy a more powerful laptop.  [Rule #2](http://technicalagain.com/what-are-we-doing-here/ground-rules/) grounded me.  I'm glad I fought that urge and enjoyed the classical challenge of giving this laptop a new future.
