---
author: kylepott
date: 2018-11-14 02:58:08+00:00
draft: false
title: Automating System Monitoring and Alerting with LogWatcher.sh
type: post
url: /2018/11/14/automating-system-monitoring-and-alerting-with-bash/
categories:
- bash
- cron
---

Over the past several weeks I completed [this Lynda course](https://www.lynda.com/Bash-tutorials/Learning-Bash-Scripting/142989-2.html) about Bash scripting.  The course was great and I was able to put my learnings to use.  I wrote two handy bash scripts: the first is an open source project on GitHub I created called [LogWatcher](https://github.com/kylepott/LogWatcher).  The second is still a work in progress, but can be used to scan database exports and system logs to identify if sensitive data is stored in plain text.  I'll focus on describing the benefits of LogWatcher.

![](https://technicalagain.com/wp-content/uploads/2018/11/Screenshot-from-2018-11-13-21-03-58.png)


I wrote LogWatcher as a utility to perform automated monitoring and alerting for my [password manager](https://technicalagain.com/2018/04/05/rolling-my-own-password-manager-part-2/).  My password manager already has a great event logging architecture, but it doesn't have any monitoring or alerting for adverse behavior.  So, LogWatcher simply watches the error log for any anomalous behavior.  If someone attempts a log in or someone attempts to read the database or otherwise try any URL hacking the error log will pick it up and then LogWatcher will send me an email alert.

There are really two versions of LogWatcher.  The first is designed if you are hosting your own server so it relies on pre-configuring SMTP.  The second flavor, LogWatcherBlue.sh, is intended to be uploaded to a web host and relies on the cPanel default email configuration.  Of course, you can always edit the script to send the email to your wireless carrier's SMS gateway and receive a text message.

**LogWatcher Design
**

LogWatcher is a bash shell script, that does the following:

1.) Connects over SSH into the home directory of the web server.

2.) Downloads a copy of the error_log

3.) Compares the error_log to a previous iteration to see if the contents differ - indicating activity (expected or adverse) within the password manager.

4.) If activity is detected, an alert email is sent with the date and time.

5.) LogWatcher can be run ad-hoc, but it is really intended to be loaded into Cron and scheduled to run at any interval of your choosing.  I have it set to compare the error_log every minute which essentially provides continuous monitoring and alerting - overkill!

**Learnings**

It's important for the error_log to be secured behind a .htaccess file.  If the error_log sat in the open internet it would defeat its purpose by providing any attacker with the kind of helpful information that would enable their attacks.  This is why we connect with SSH rather than over the open web.

[Here's a great technique](https://www.howtogeek.com/66776/how-to-remotely-copy-files-over-ssh-without-entering-your-password/) to connect over SSH using the private key so you don't have to enter your password manually.  Once this is configured LogWatcher runs in a fully automated fashion.

LogWatcher could be expanded for more features but two notable ones to consider would be: adding a grep search phrase to alert only when specific activity is detected.  LogWatcher could also clean up the error_log so it doesn't grow so large.

I welcome your input and thanks for checking out [LogWatcher](https://github.com/kylepott/LogWatcher)!
