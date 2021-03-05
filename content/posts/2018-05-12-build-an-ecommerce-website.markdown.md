---
author: kylepott
date: 2018-05-12 01:11:17+00:00
draft: false
title: Build an eCommerce Website with WooCommerce
type: post
url: /2018/05/12/build-an-ecommerce-website/
categories:
- Projects
- ProjectSuccess
- Stripe
- WooCommerce
- WordPress
---

![](https://technicalagain.com/wp-content/uploads/2018/05/Screenshot-20180511192617-1249x620.png)


I spent the last three weeks designing, building, testing, debugging and putting the finishing touches on my first eCommerce website, complete with a full shopping cart experience and product purchase workflow.  One of my original [project goals](https://technicalagain.com/what-are-we-doing-here/ground-rules/sample-page/) in launching this site was to learn how to take a payment online.  This turned out to be relatively straight forward.


<blockquote>This project would have been all but impossible in 1998 and still very, very challenging in 2008.  In 2018, I didn't even write a single line of code.</blockquote>


I considered three possible approaches for this project: Wordpress with WooCommerce, Bootstrap with a shopping cart add-in, and Shopify.  I ultimately decided on WooCommerce for two reasons: there was an overwhelming number of different shopping cart options within the Bootstrap community.  Although they are reasonably well supported, they couldn't match the centralized level of community support available through WooCommerce.  The second reason I settled on WooCommerce was that the actual implementation of payment options were sufficiently abstracted from the code - which appealed to me.  Bootstrap is more customizable, but from what I could tell would require me to setup my own piping to test and establish the payment workflow.  Bootstrap may be more appropriate for a large scale legitimate online retailer, but seemed too complex than what I needed for a single product sole proprietorship.  I turned away from Shopify due to the recurring fee structure.

The installation of WooCommerce started by first installing WordPress, then adding the WooCommerce plug-in, and then using the guided WooCommerce installation process to pick payment options.  Originally, I decided to use Stripe and PayPal, but ended up backing off PayPal because I felt it was sufficiently redundant to the features included in Stripe.  Knowing data minification is a technique to reduce the possibility of breach I decided to just use one payment system and can always add in PayPal if warranted in the future.  WooCommerce has a very smooth installation process.

I finished by picking a theme and stylizing the site, integrating Google Analytics, customizing the product description and pricing, nailing down the cart and checkout workflows, and finishing with the "after sales" experience--which was basically just a follow up email.  I also setup  Google AdWords.  The pricing for Stripe is very affordable, something akin to 3% per transaction plus 30 cents and no recurring fees.  WooCommerce can make some improvements.


## Learning


This was a good and straight forward project. WooCommerce is satisfactory, but not a great product yet.  There were a number of features I'd expect to be customizable right out of the box but instead required me to install additional plug-ins (some free and some proprietary) or do some hacking deep into the configuration files.  Three examples come to mind:



 	  1. To change the text on the "Add to Cart" button to say "Buy Now"
 	  2. To customize the "purchase confirmed" email
 	  3. To rearrange where the price shows up--whether above or below the product description

I was also disappointed that WooCommerce does not have a built in visitor tracking/analytics or marketing package-s-requiring me to, you guessed it, install yet another  batch of plug-ins.

After getting reasonably familiar with WooCommerce and participating in the community I noticed that it is not uncommon for administrators to have up to 30 or 40 different plug-ins running for a single WooCommerce site.  That makes debugging really hard, keeping the plug-ins up-to-date almost impossible, and adds a lot more opportunities for defects and breach.  Room for improvement, I think, for sure.

I didn't have any real technical snags or frustrations, and I appreciated having the chance to learn about staging servers, testing the purchase process, applying a digital certificate (yet again), and a dash of search engine optimization and internet marketing.

It is truly amazing that we live in an era that a team of one guy can buy a domain name and hosting, get a digital certificate,  build a website and shopping cart, and can create an internet business in under three weeks for less than $80.  Eric Ries talks about this concept in his book _The Lean __Startup_ ([summary](http://www.kimhartman.se/wp-content/uploads/2013/10/the-lean-startup-summary.pdf)) but it never really hit home for me how truly accessible technology is until I did this project.  We live in an amazing time!  This project would have been all but impossible in 1998 and still very, very challenging in 2008.  In 2018, I didn't even write a single line of code.
