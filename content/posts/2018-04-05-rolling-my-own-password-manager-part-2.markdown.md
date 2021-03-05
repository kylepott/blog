---
author: kylepott
date: 2018-04-05 02:25:52+00:00
draft: false
title: Rolling My Own Password Manager (Part 2)
type: post
url: /2018/04/05/rolling-my-own-password-manager-part-2/
categories:
- Password
- Projects
- ProjectSuccess
---

Continuing the review of how I implemented my own password manager, this is part two.  If you'd like to read part 1, you can do so [here](https://technicalagain.com/2018/03/31/rolling-my-own-proper-password-manager/).  For somewhat obvious reasons I am not going to share the product name or the specific details about my implementation broadly here.  I would be glad to provide a bit more information: if you are so interested, leave a comment below and I can reply to your question directly.

I picked a product that fit the following desirables:



 	  * Standalone install on my own server - does not rely upon any third party
 	  * Open source and more than 10 years old.  Reasonably active developer community, penetration tested and uses proven encryption algorithms.
 	  * The installation was modular allowing me to customize the front- and back-ends I wanted to use.
 	  * The solution has logging in place so I can monitor log in attempts.



# Stumbling Blocks


I mentioned in [part 1](https://technicalagain.com/2018/03/31/rolling-my-own-proper-password-manager/) that I had two remaining control efficiencies which I can share now as I have those patched up.  The first issue was a silly mistake.  I had uploaded into my password manager the username and password for the server that hosts the password manager itself.  The issue here is that if the password manager was ever breached and the data stolen, by including the credentials of the host server, a malicious actor could then delete the password manager itself leaving me in a world of hurt.  I have since deleted those credentials.

The second issue I realized was that I never had a certificate attached to the server leaving me vulnerable to possible man-in-the-middle attacks.  Since one of the pleasures of using a password manager is that I can log in to copy/paste my credentials from my laptop or phone, the chance of using the password manager on a public access point is pretty high.  So I signed up for a free certificate from [Let's Encrypt](https://letsencrypt.org/) to encrypt all the traffic.  My host made it extremely easy to apply the certificate.


# **Learnings**


I had a few challenges in this project.  For one thing, I had a really difficult time forwarding all traffic to use https instead of http after I got my certificate installed.

I was finally able to get forwarding to work by adding the following lines to the _.htaccess_ configuration file located at the root of the public directory.

    
    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
    RewriteCond %{HTTPS} off
    RewriteRule ^(<directory name>.*)$ https://www.domainname.com/sub-directory/sub-directory/sub-directory/etc.$1 [L,R=301]


This was particularly nasty because I had intended to use an ._htpasswd _configuration on the server to require "double credentialing" - one where you log into the directory containing the password manager and one where you log into the password manager itself.  The forwarding rules and the authentication rules for Apache kept stepping on each other and so I decided to abandon the directory authentication.  I definitely lost a lot of time and effort on this, but since directory level authentication in Apache isn't really secure anyway, I decided to cut my losses.

Another less challenging but important learning was to turn off web crawling using a _robots.txt_ file.  I realize this provides limited control utility, but why have search engines indexing my password manager?  That only creates more visibility and opportunity for malicious actors to find it and attempt exploits on it.  I know that malware crawlers can and do simply ignore _robots.txt_ configurations, but I also know that utilities like [amass](https://github.com/caffix/amass) use legitimate search engines that do respect _robots.txt _for intel.  Again, why make it easy?

Amass searches Internet data sources, performs brute force subdomain enumeration, searches web archives, and uses machine learning to generate additional subdomain name guesses.  I am going to do some experimentation with amass on my own servers to get more familiar.


# Further Work


This has been a fun project.  I have learned a lot and vastly improved my web security and habits.  I have a few more ideas that I plan to work on related to the password manager:



 	  * I am going to minify the entire application by removing any reference to its name or any other identifiers in the source code.  It will still be possible for bots to fingerprint my use of the application, but it will take more work for any malicious actors because the basic search phrases and configurations won't work on my instance.
 	  * I am still not pleased with the complexity of the passwords I used for the front and backends to communicate - so I'll add more hardening there.  I am also in the process of turning two factor authentication on for all of my assets and need to finish up activating the last few.
 	  * I also need to come up with a backup plan for two factor authentication in the event that my phone is lost or broken.
 	  * I am going to experiment with [John the Ripper](http://www.openwall.com/john/) to test the encryption and try to crack my own passwords.
 	  * I would like to set up a service to download my log file every few minutes, compare it, and send me a text message whenever there is new activity.  That way I am aware of any brute force login attempts that did not originate from me or any other approved user.

