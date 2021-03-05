---
author: kylepott
date: 2018-04-17 01:40:37+00:00
draft: false
title: Setting Up A New Ubuntu Linux Server
type: post
url: /2018/04/17/setting-up-a-new-ubuntu-linux-server/
categories:
- Server
- Ubuntu
---

![](https://technicalagain.com/wp-content/uploads/2018/04/Screenshot-from-2018-04-16-20-32-04-1024x640.png)


I have plans to start a second open source project that will need a server so over the past few days I re-purposed an old Windows laptop into a server running Ubuntu Linux.

The installation was a little tricky because after I downloaded the Ubuntu installation file, I discovered that the DVD burner on this old laptop was no longer working. Instead, I needed to create a bootable USB. [Rufus](https://rufus.akeo.ie/) is a great utility that made this very fast and easy.  I deleted an old recovery partition, added a 1 GB swap partition for virtual memory and loaded Ubuntu into the remaining free space.  I preserved the Windows partition and can now dual boot between the Ubuntu and Windows operating systems.

I created a new user account and landed on the third rung of the [Password Ladder](https://www.linkedin.com/pulse/password-ladder-kyle-pott).  I configured SSH to access the server remotely and I am good to go.

I plan to make a few more configuration changes so the server stays awake persistently. I plan to turn off the Ubuntu GUI and configure the SSH server to start on login.  For now I've got enough traction to get started on my open source project.
