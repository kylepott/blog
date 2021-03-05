---
author: kylepott
date: 2019-03-11 16:25:58+00:00
draft: false
title: Information Lifecycle Management (ILM) in AWS with S3 Glacier and Lifecycle
  Rules
type: post
url: /2019/03/11/information-lifecycle-management-ilm-in-aws-with-s3-glacier-and-lifecycle-rules/
---




For a few months now I've been meaning to put an automated rule in place to save money by moving untouched S3 data over to S3 Glacier.







[I previously wrote about how I set my personal blog to backup to AWS the first of every month](https://technicalagain.com/2018/09/28/moving-a-backup-copy-of-wordpress-over-to-aws-s3/).  It was a fun project, but I began experiencing a micro-chasm of what real businesses experience: the first month my bill was $1, the second month $2, and now by the fourth month, $4.  No biggie when you're just one guy with a personal blog, but the relevancy of this exercise for a real company is obvious.







Every month I add an additional ~35GB into S3.  I have this fully automated so no action taken by me - except to pay the monthly bill.  Which is also automated - ha!





![](https://technicalagain.com/wp-content/uploads/2019/03/Screenshot-from-2019-03-11-11-20-44-1024x423.png)






This was a quick project.  I created a new Lifecycle Rule in the management tab within S3, set my object creation target to Glacier (cheapest option) and set the rule to move my files over within 5 days and any previous versions of the files over within one day.  I set the rule to cleanup any modified or damaged uploads and set the rule to run.  It will now run daily.





![](https://technicalagain.com/wp-content/uploads/2019/03/Screenshot-from-2019-03-11-11-11-02.png)




![](https://technicalagain.com/wp-content/uploads/2019/03/Screenshot-from-2019-03-11-11-13-20.png)




![](https://technicalagain.com/wp-content/uploads/2019/03/Screenshot-from-2019-03-11-11-14-18.png)




![](https://technicalagain.com/wp-content/uploads/2019/03/Screenshot-from-2019-03-11-11-18-35-1024x338.png)


