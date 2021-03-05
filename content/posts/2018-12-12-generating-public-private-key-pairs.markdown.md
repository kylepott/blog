---
author: kylepott
date: 2018-12-12 13:53:37+00:00
draft: false
title: Generating Public/Private Key Pairs
type: post
url: /2018/12/12/generating-public-private-key-pairs/
categories:
- crypto
- ecdsa
---


![](https://technicalagain.com/wp-content/uploads/2018/12/Screenshot-from-2018-12-12-07-45-27.png)






My public key is copied at the bottom of this post. I used ecdsa instead of RSA due to the exponentially longer time it would take to brute force--and at a size of 521 bits that should be practicably impossible. Great write up on the topic [here](https://www.ssh.com/ssh/keygen/).







_As with elliptic-curve cryptography in general, the bit size of the public key believed to be needed for ECDSA is about twice the size of the security level, in bits. For example, at a security level of 80 bits (meaning an attacker requires a maximum of about 2^80 operations to find the private key)._







_ _



















ecdsa-sha2-nistp521 AAAAE2VjZHNhLXNoYTItbmlzdHA1MjEAAAAIbmlzdHA1MjEAAACFBAD2RCeJQb/fwNGwYDFTbVbDcNYSDpj9xnaDGzbmcrPHDhRjzf6uhlXYyhQXASvhGVsmCWLSyFshspZa56/p1T4KdQFUa1CJ6fABN4T4YJDoRMLYmVNt8763UjjmBWUb1tSV0yuBCToqf15nhrc0r3svN6ZZQzAJvCmmlW3WSBUq3p4f5g== delf@delf-MacBookPro











  








  




