---
author: kylepott
date: 2018-12-03 20:57:24+00:00
draft: false
title: Credential Stuffing with Cr3dOv3r
type: post
url: /2018/12/03/credential-stuffing-with-cr3dov3r/
categories:
- cr3dov3r
- python
---

![](https://technicalagain.com/wp-content/uploads/2018/12/Screenshot-from-2018-12-03-14-09-17.png)
After the [Dunkin Donuts credential stuffing breach](https://latesthackingnews.com/2018/11/30/dunkin-donuts-resets-passwords-after-enduring-credential-stuffing-attack/) I went on the lookout for a tool to search for and find leaked credentials.  I came across [Cr3dOv3r](https://github.com/D4Vinci/Cr3dOv3r), a nice little Python script that let's you search for an email address to see which sites leaked it and when. It also let's you search to find out if a plaintext password was leaked.  You can then enter the leaked password, or any password of your choosing, across a broad array of sites and the utility will automatically test to see if it is still valid.

A simple tool and could also be applied nicely in an enterprise environment to proactively detect email addresses that were leaked.
