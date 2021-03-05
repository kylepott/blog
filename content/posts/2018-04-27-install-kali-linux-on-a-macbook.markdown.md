---
author: kylepott
date: 2018-04-27 02:01:23+00:00
draft: false
title: Install Kali Linux on a MacBook
type: post
url: /2018/04/27/install-kali-linux-on-a-macbook/
categories:
- Kali
- Linux
---

I installed Kali Linux on a dualbooted MacBook Pro last week. The frst thing I did was delete unnecessary files on the Mac to free up space and then shrunk the size of the partition using Apple's built-in Disk Utility. I then manually installed Kali on the remaining unused portion of the hard drive.

This wasn't a particularly challenging project but it wasn't easy either. The only real issue I experienced was related to my bootable USB hard drive. I used a utility called Rufus to turn the _Kali.iso_ file into a bootable install on an external hard drive.  I messed up a configuration setting on Rufus, though. Although I could boot Kali into "live mode" just fine, I could only get about half way into the installation until Kali could not detect my CD-ROM. You'd think this wouldn't be a big deal, but a material part of the installation occurs when the contents of the USB drive are mounted and copied into a folder called /_cdrom_ and the installer is "faked" into thinking the data is coming from a CD/DVD rather than a thumb drive.  I tried to mount and create the directory manually and move the contents in, but I was unable to get past this point.  So back to the drawing  board.  This time I used Apple's built in dd terminal utility to create the bootable USB and the install went much smoother.

Once I got Kali installed, I noticed a few more odd things.  Example, the mouse did not work during the install, but worked fine after.  The /etc/apt/sources.list was blank.  When I added a new non-root user, I had to log out and log back in before I could see the user even though I was logged in as root.  Once the new user was created, he wasn't part of the sudoers file.  Not a big deal there, but one more step I had to follow up on.  Overall ease of installation and first use I would give a score of about 7/10.

After playing with Kali for about three days now, I am really excited about all the penetration testing tools to learn, but I can't say the experience is much better or worse really than when I have used the GNOME desktop on other Linux distributions like Ubuntu or Fedora.

My home network is really coming together now.  I now have access to Windows and Mac desktops, I have a nice Ubuntu server setup and my main machine is Kali running on a late 2011 MacBook.  We continue to abide by the [ground rules](https://technicalagain.com/what-are-we-doing-here/ground-rules/) by doing the work ourselves and breathing new life into old things.  More fun ahead.
