---
author: kylepott
date: 2019-02-26 02:58:16+00:00
draft: false
title: Exfiltrating Data from MySQL and Postgres
type: post
url: /2019/02/26/exfiltrating-data-from-mysql-and-postgres/
tags:
- kali
- msf2
- mysql
- netcat
- postgres
---




I continued experimenting with Metasploitable 2.  Over the past few days I managed to gain access to the MySQL and Postgres databases and used _net cat_ to dump the databases and export them.







Using a similar technique [as before](https://technicalagain.com/2019/02/20/got-root-two-more-exploits/), I used a reverse shell exploit to control the host, I launched mysql, queried the database to view the users, and found that two users didn't have passwords.





![](https://technicalagain.com/wp-content/uploads/2019/02/Screenshot-from-2019-02-21-16-28-40.png)






I then used the guest account to dump the tables into a zip file and used _net cat_ to send the file from the host over to my attacker.





![](https://technicalagain.com/wp-content/uploads/2019/02/Screenshot-from-2019-02-21-20-24-54.png)




![](https://technicalagain.com/wp-content/uploads/2019/02/Screenshot-from-2019-02-21-20-25-09.png)
After 





After the file arrived, I unzipped it and could see the contents from the user table within the dvwa database.





![](https://technicalagain.com/wp-content/uploads/2019/02/Screenshot-from-2019-02-21-16-34-58-1024x160.png)






I repeated a similar chain of events for the Postgres databases.  I was able to find the list of users, change the password for the main Postgres account, browse the tables, and then log in directly using the psql exposed service.  Nothing noteworthy in the tables so I skipped dumping them.





![](https://technicalagain.com/wp-content/uploads/2019/02/Screenshot-from-2019-02-21-20-30-01.png)






Overall, this was a good project.  I have also been working on maintaining presence and installed two backdoors.  More on that tomorrow maybe...  




