---
author: kylepott
date: 2018-09-23 13:56:20+00:00
draft: false
title: Ghost on AWS - success!
type: post
url: /2018/09/23/ghost-on-aws-success/
categories:
- aws
- ec2
- ghost
- MySQL
- Projects
- ProjectSuccess
- Ubuntu
- WordPress
---

![](https://technicalagain.com/wp-content/uploads/2018/09/gnome-shell-screenshot-1KBXPZ.png)




This is the third and final part of my first foray into AWS.  You can read [part 1](https://technicalagain.com/2018/09/18/first-foray-into-aws/) and [part 2](https://technicalagain.com/2018/09/20/more-aws/).  AWS is great.  Getting access is secure and easy and you can't beat free. AWS is incredibly quick at spinning up  new instances and once connected over SSH it is extremely fast - it rivals the feel of a local installation - almost no latency for me.

After getting Ubuntu installed, I spent the last few evenings attempting to install Ghost per [these instructions](https://docs.ghost.org/docs/install).  [Ghost](https://ghost.org/) is still an early work in progress. I had a lot of challenges. For example, the presence of a simple `.config` file blocked the installation until I deleted it.  During the installation, file premissions kept changing between my account and the newly installed Ghost account.  This is what ultimately blocked me completely.  No amount of `chown` or `chmod` adjustment would make Ghost work.  I tried every conceivable combination of ownership for `/var/www/ghost` including my account, the ghost account, and adding both to `sudoers`.  The only thing I stopped short of was changing the ownership to root which just didn't seem appropriate.

I ended up abandoning my own attempt to install Ghost and instead tried out the [Bitnami installation of Ghost](https://docs.bitnami.com/aws/apps/ghost/).  This is a pretty cool capability within AWS - essentially an "app store" with Amazon Machine Images (AMIs) that you can install for free (or purchase).  The AMIs are customized for single or multiple needs.  In my case, Bitnami created a custom AMI with just Ghost installed.  I spun it up and had Ghost running in under five minutes.  All configuration worked out of the box - even punching a hole in UFW - Uncomplicated Firewall so you can navigate to the browser right out of the box and Ghost just works.  That is pretty cool!  It would be great for the Ghost team to launch their own AMI instead of relying on Bitnami. I think Automattic should consider doing the same with WordPress.


## Thoughts on Ghost


Ghost is built with a a good value proposition in mind: a more modern and faster architecture than WordPress and keeping the feature set to just the essential.  I agree that over time WordPress has developed some bloat - both in terms non-essential features and UI clutter.

Ghost has a few drawbacks that I'm sure the team is working on.  For one, the installation process needs to be streamlined.  I'm pretty proficient at Linux having over 15 years experience with Ubuntu and I couldn't get the install to work.  There is a wide gap between the installation process for Ghost and the "World Famous" five minute install for WordPress.

The universe of available hosting platforms is very small.  I can understand this approach because Ghost is basically betting big on AWS - which makes sense to me.  The architecture of Ghost has a few drawbacks in my opinion.  For example, to install a new theme you have to reboot the server.  Not surprising, but since Ghost is so new, the ecosystem of plugins, themes, and other capabilities is nowhere near the universe of extensions available to WordPress.

In general, the UI and blogging experience is clean and simple, but not remarkably different than WordPress, in my opinion anyway.

A few benefits worth noting.  Relative to my current situation, Ghost on AWS allows full control of the server.  From a security perspective, this would allow me to control and monitor the entire server and firewall configurations.  That moves the responsibility for controls from my hosting provider to me.  I would like that.  As with all AWS appliances, Ghost has the potential to be a fair bit cheaper than a traditional WordPress blog on a regular domain host - but that depends hugely on the amount of traffic and purpose of the blog.

In total, Ghost is an interesting idea, I really like how it is "designed" for AWS.  But the install is too complex, the architecture needs some continuous improvement and the ecosystem needs to keep growing.  I would consider this project more frustrating than fun - messing with file permissions over and over not really all that enjoyable!  For now I won't be migrating this blog over to Ghost, but I'll keep an eye on how the product matures over time.


