---
author: kylepott
date: 2018-03-31 14:54:36+00:00
draft: false
title: Rolling My Own Proper Password Manager (Part 1)
type: post
url: /2018/03/31/rolling-my-own-proper-password-manager/
categories:
- Password
- Projects
- ProjectSuccess
---

On previous posts here I shared my poor hygiene when it comes to password management (reusing the same password and not having passwords complex enough). I'm really happy to say I've made some major improvements. I've been meaning to roll my own password manager and I had a few requirements in mind.

1.) I wanted to host the web application myself on my own server so I could access it from any device and share access with my spouse.

2.) I wanted a password management application that would make it easy to generate maximum complexity usernames and passwords that I could copy and paste.

3.) I wanted the password manager to be free standing and not rely on any cloud or external services outside the scope of one of my servers.

4.) I wanted an open source solution, relying on established encryption protocols.

The primary attack vector that I am guarding against is breaches at the various third party sites I use - take the recent breach at MyFitnessPal as an example. This impacted me personally due to too much password-reuse. I am on a quest to eliminate both password and username re-use as well as start enabling two factor authentication on my email and sites with my financial assets. I am not concerned, primarily, about the physical security of my devices - which means I use Chrome and allow the passwords to be saved and even allow Chrome to sync across devices.

Overall the solution has a pretty nice experience. I use my password manager to generate random usernames and passwords and then copy and paste them when I need to. Chrome then saves the username and password and I don't have to worry about it again.

In this post I am not going to share which solution I picked, where I installed it, or what customization I made in this post. I still have two control gaps in the solution I have implemented. I will share more details once I have those patched up in the next couple of weeks.
