---
author: kylepott
date: 2018-09-18 01:46:09+00:00
draft: false
title: First Foray Into AWS
type: post
url: /2018/09/18/first-foray-into-aws/
categories:
- aws
- ec2
- ghost
---

![](https://technicalagain.com/wp-content/uploads/2018/09/gnome-shell-screenshot-FV61PZ.png)


Tonight I started the journey into Amazon Web Services (AWS) for the first time.  First, I signed up for a personal (free!) EC2 instance.  My plan is to install the [Ghost blogging platform](https://ghost.org/), add a domain name and DNS.  Ghost looks pretty cool.  Minimal, fast, and will give me a chance to get more familiar with an open source JavaScript architecture I have not used much: Ember.js, Node.js, and Express.js.

This project will require access to the AWS Command Line (CLI).  So the next step was to setup access management within EC2 and create an account with programmatic access which enables an access key ID and secret access key for the AWS API, CLI, and more.  AWS has nice features for creating user groups and permission boundaries.  I am essentially creating a synthetic root user, so no need to setup these capabilities yet.

Amazon takes up to 24 hours to spin up a new instance...so I wait...more soon.
