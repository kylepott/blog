---
author: kylepott
date: 2017-11-26 14:32:14+00:00
draft: false
title: Dual Boot GalliumOS on a Chromebook
type: post
url: /2017/11/26/fully-installing-linux-on-a-chromebook/
categories:
- chromebook
- chrx
- Projects
- ProjectSuccess
- Ubuntu
---

[
  ![](https://imgur.com/XP6LFjdl.png)

](https://i.imgur.com/XP6LFjd.png)
I had some success [running Ubuntu on my Chromebook](http://technicalagain.com/2017/11/11/run-ubuntu-linux-on-a-chromebook/) through Crouton, but I started running into issues.  My hypothesis is that since aspects of the Linux kernel are shared between ChromeOS through chroot with Crouton, I couldn't get a clean installation of Apache to run. I assume this was due to permissions.  So I set out on yet another Linux adventure to do a true installation of Linux on the Chromebook.

I found a nice utility called [chrx](https://github.com/reynhout/chrx) that made the installation very straight forward.




<blockquote>Installing Linux via chrx onto a new (or freshly recovered) Chromebook is a two-phase process:

The first phase reserves space on your SSD or other storage device for the new operating system, and then reboots.

The second phase installs your chosen distribution, and configures the new system according to your selected options.</blockquote>



The installation proceeded smoothly by typing the following into the terminal.
`Run chrx: cd ; curl -Os https://chrx.org/go && sh go`

Follow on-screen instructions to prepare your Chromebook for installation



### Stumbling blocks


I have a Bay Trail chromebook.  I should have paid more attention.  I did not notice this the first time I installed so even though the install went smoothly, when I pressed `CTRL + L` to launch into Ubuntu, it was non-responsive and would boot back into ChromeOS.  The issue was that I needed to update my firmware.  I found this nice [firmware update script](https://mrchromebox.tech/#fwscript). I chose the first option which installed the RW_LEGACY firmware with a newer/working/customized version of the SeaBIOS firmware payload and then I good to go Ubuntu loaded nicely.

A second issue I ran into was that the full Ubuntu 16.04 install was just a bit too resource heavy for my now [discontinued Acer Chromebook](https://www.amazon.com/gp/product/B00MMLV7VQ/ref=oh_aui_search_detailpage?ie=UTF8&psc=1).  Chrx comes with a variety of different distro installation options.  I chose to go with GalliumOS. Gallium is built on Ubuntu and optimized for Chromebooks plus it has a very clean design.  

My install of Apache, PHP, MySQL, and MongoDB all went smoothly so I have a nice and pretty responsive development environment.  I have not really booted into ChromeOS since installing Gallium.

Thanks to [reynhout](https://github.com/reynhout) for their work on chrx, [MrChromeBox](https://twitter.com/mrchromebox) for the firmware script, and [hugegreenbug](https://www.reddit.com/user/hugegreenbug) the founder of the Gallium project.  This is another example project demonstrating the remarkable power of open source software.
