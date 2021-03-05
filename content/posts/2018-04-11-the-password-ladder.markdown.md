---
author: kylepott
date: 2018-04-11 01:16:12+00:00
draft: false
title: The Password Ladder
type: post
url: /2018/04/11/the-password-ladder/
categories:
- Password
---

![](https://technicalagain.com/wp-content/uploads/2018/04/ladder-223x300.jpeg)
Where are you on the Password Ladder and what can you do to move one rung higher?

**You're standing next to the ladder, holding it** if you are using one of the world's most [common passwords](https://en.wikipedia.org/wiki/List_of_the_most_common_passwords) like _123456_, _password_, _qwerty_, _123456789_, or _letmein_.  Amazingly, even in 2018, 8-10% of people still use these most basic of passwords.  If your username is discovered, your password is immediately compromised by even the simplest of dictionary attacks. Heck, you don't even need a dictionary to guess the password.  Forget about if just the password hash is discovered or an encrypted version of the password is acquired.  You're sunk no matter what.

**You're on the first rung of the ladder, **if you are reusing the same username and password combination on the majority of the websites you visit.  This is especially problematic if the credentials you use for your bank account or email address are not unique.  Most email accounts serve as a gateway to other account credentials.  If you're on the first rung of the ladder, basically any website getting hacked puts in jeopardy your identity and financial assets.

**You're on the second rung of the ladder**, if you are reusing the same username and a password that is made up of a basic combination of personal information like your children's names and your anniversary date.  The second rung is barely any better than the first rung.

**Third rung **if you are using a single base word and then substituting special characters and capitalization instead of random word combinations. Thank you [xkcd](https://xkcd.com/936/).  No simpler way to describe this than below.

![](https://imgs.xkcd.com/comics/password_strength.png)


If you made it here you are in the top 5%. The **fourth rung **has two factor authentication turned on for important accounts like your email, bank, benefits, and retirement vehicles.  Incredibly, it is estimated that only 5-10% of people have voluntarily enabled two factor authentication on Gmail even though it has been available for a number of years.

**Top of the ladder **if you are randomly generating usernames and passwords (not reusing them), you have two factor authentication turned on and you are using a structured approach to manage your passwords like using a password manager or browser autocomplete to make sure your passwords are maximum length and complexity.

Please remember that there is no perfect system. Even the fifth rung here can be debated about whether the use of password managers and browser autocomplete provide additional security or if they introduce additional risk vectors. The debate is warranted, but I believe the benefits outweigh the risks. Just know that no approach is impervious to all attacks and keep in mind:








1. Phishing attacks actually work.




2. Credential theft via phishing and administrator credential theft are the most common way external actors gain access.




3. Social engineering attacks (pretext calling), over the shoulder snooping, and man-in-the-middle attacks are still a very effective way to steal credentials.




4. Many people still write their passwords down, store them in text documents on their hard drive or server, or hard code passwords into source code and stored procedures. This includes storing encryption keys in the same folder as the encrypted material.




5. If there is data loss or ex-filtration, it is much more likely to come from an internal actor's intentional or unintentional activities (mis-configurations, forgetting to encrypt, copying the whole file instead of one record, etc.).




6. Zero day (undiscovered defects) happen only 1-5% of the time. It is much more common that a known defect will be exploited. Some known defects are aged 5 or more years and still unpatched in production. Bad actors scan and fingerprint unpatched defects and they have open source exploit kits to take advantage of the defect once spotted. Malicious actors don't even have to be that technical to be effective.






Control what you can and take necessary precautions.  Move yourself up one rung of the ladder.


