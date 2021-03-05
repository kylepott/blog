---
author: kylepott
date: 2018-09-28 22:39:13+00:00
draft: false
title: Moving a backup copy of WordPress over to AWS S3
type: post
url: /2018/09/28/moving-a-backup-copy-of-wordpress-over-to-aws-s3/
categories:
- aws
- Projects
- S3
- WordPress
---

![](https://technicalagain.com/wp-content/uploads/2018/09/gnome-shell-screenshot-UCKWPZ.png)


Today I set out to make a complete backup of my WordPress blog, archive of the images and all.  I set out to move the backup from my domain host directly into Amazon S3.  Eventually, I plan to set a policy within S3 to move the files over to Amazon Glacier for even cheaper storage.  We'll start with the AWS portion, then the WordPress portion.


## **AWS**


I created a new user, _me_, and then I created a new group, with a new policy--essentially giving myself read, write, and credential creation permissions specifically for S3.

I headed over to S3 and created a new bucket for WordPress backups. I turned on logging, and I turned on encryption for the bucket.  One thing I found strange (and I might have this wrong) was that I had to name my bucket something unique relative to all S3 buckets and not just those in my account.  So for example, for some reason I had to name my bucket WordPress-s3s3s3 because WordPress and WordPress-s3 were already taken, but not by me.

I went back into Identity and Access Manager (IAM), created myself a new access ID and secret key and was ready to roll.


## **WordPress**


In WordPress I installed the extension BackWPup.  I then chose my correct AWS region (after a failed attempt), entered my key ID and secret key, picked my S3 bucket, elected to use encryption, chose a storage type as "rarely access," to help control costs, and scheduled the job to run.  BackWPup allowed me to create a compressed archive and move the file over in 20MB chunks to prevent the transfer from being blocked by the ISP for being too large.

I changed the compression to TarGz after some research and found it offers the fastest compression ratio (though the remaining file is larger).  The compression alone has been running a long time - we have several thousand photos in the family blog and over 600 folders so I expect this could take over an hour just to compress.  We will see how it goes.  I also plan to monitor if I breach the free pricing tier at AWS.  The total _compressed _file size ended up over 34GB!!

Within BackWPup I set WordPress cron to schedule the job to run every month at 3am.

As I've said in my previous posts on AWS, I am amazed by the technology.  Once getting the permissions up and running, it has worked exceptionally well.  The reliability and speed are impressive.

![](https://technicalagain.com/wp-content/uploads/2018/09/gnome-shell-screenshot-342HPZ.png)




_Update_

After compressing for about 30 minutes, I'm happy to say the job completed successfully and my backup is sitting safe and sound in S3!

![](https://technicalagain.com/wp-content/uploads/2018/09/gnome-shell-screenshot-MBAOPZ.png)

