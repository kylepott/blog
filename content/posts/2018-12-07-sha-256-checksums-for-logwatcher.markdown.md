---
author: kylepott
date: 2018-12-07 20:14:48+00:00
draft: false
title: SHA-256 checksums for LogWatcher
type: post
url: /2018/12/07/sha-256-checksums-for-logwatcher/
categories:
- LogWatcher
- Open Source
---

The more I was thinking about it, since [LogWatcher](https://github.com/kylepott/LogWatcher) is a server utility and may occasionally  be run with escalated privileges, I thought it would be wise to publish checksums for integrity.

_LogWatcher is a utility to perform very simple automated system monitoring and alerting. It is an ideal solution to use in conjunction with a web app that has a sound event logging architecture implemented. LogWatcher simply watches an error log file for any anomalous behavior. If someone attempts a log in, attempts to read the database, hack the URL, or any other adverse behavior that is landing in an error log file, LogWatcher can send an email alert to make you aware._

sha256sum for logwatcher.sh:
9d7dfcf0d6dceabddf272fd45bbab26f7a9008e38f467eb7f24a42d8d387842b

sha256sum for logwatcherblue.sh
ba346500fa59969fc739def6c5f3d68f60b40840915b3d701692dd46eeca2e56

![](https://technicalagain.com/wp-content/uploads/2018/12/Screenshot-from-2018-12-07-14-10-28.png)


_The program sha256sum is designed to verify data integrity using the **SHA**-**256** (**SHA**-**2** family with a digest length of **256** bits). **SHA**-**256** hashes used properly can confirm both file integrity and authenticity. **SHA**-**256** serves a similar purpose to a prior algorithm recommended by Ubuntu, MD5, but is less vulnerable to attack._
