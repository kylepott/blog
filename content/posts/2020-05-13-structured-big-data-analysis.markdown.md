---
author: kylepott
date: 2020-05-13 16:52:52+00:00
draft: false
title: Structured Big Data Analysis
type: post
url: /structured/
categories:
- python
tags:
- data science
- github
- terminal
---




I completed the [Programming for Data Science with Python](https://www.udacity.com/course/programming-for-data-science-nanodegree--nd104) nanodegree at Udacity.  The program was outstanding. It  was formatted in a way that I really like to learn: a short video lesson, a short text recap/expansion of the content, and then a portion to practice what you learned.  This course had three main technical objectives and two capstone projects.







**Focus 1: SQL, Beginner to Advanced**







The first objective was to learn SQL.  This portion included a realistic capstone project using SQL to analyze a movie rental company with multiple locations: movie categorization, rentals, customer data, employee workforce data, and payment information.  This portion of the class was excellent and moved from basic SQL all the way through the most advanced, yet practical, uses of SQL that anyone would expect to use in a real business scenario.  The capstone project required an executive summary be presented to management which I've embedded below--go full screen to see the details.  The capstone projects are independently evaluated against a rubric.







**Management Capstone Presentation**





{{< gslides src="https://docs.google.com/presentation/d/e/2PACX-1vQ7gQcEhfcbnvHoz0bB-vXCI6h4W7_g1YH3EX9iUKBOVfoYousnOAO3NecAaRst4P5NtyVlKxtf12Ys/embed?start=true&loop=true&delayms=10000" >}}




 


{{< highlight mysql >}} 
****************************
*SLIDE 1                   *
****************************
  SELECT sub.title, 
         sub.name, 
         count(rental_id) 
  FROM 
         ( SELECT i.inventory_id, i.film_id, c.name, f.title, r.rental_id
             FROM inventory i
             JOIN film f
               ON f.film_id = i.film_id
             JOIN film_category fc
               ON fc.film_id = f.film_id
             JOIN category c
               ON fc.category_id = c.category_id
             JOIN rental r
               ON r.inventory_id = i.inventory_id
            WHERE c.name 
               IN ('Animation', 'Children', 'Classics', 'Comedy', 'Family', 'Music')
         ORDER BY 3, 4
         ) sub

  GROUP BY 2, 1


****************************
*SLIDE 2                   *
****************************
  SELECT f.title, 
         c.name, 
         f.rental_duration, 
         NTILE(4) OVER (ORDER BY f.rental_duration) AS standard_quartile
    FROM film f
    JOIN film_category fc
      ON f.film_id = fc.film_id
    JOIN category c
      ON fc.category_id = c.category_id
   WHERE c.name 
      IN ('Animation', 'Children', 'Classics', 'Comedy', 'Family', 'Music')
  
  ORDER BY 3;

****************************
*SLIDE 3                   *
****************************
  SELECT DATE_PART('month', r.rental_date) as Rental_month, 
         DATE_PART('year',r.rental_date) as Rental_year, 
         s.store_id, 
         COUNT(r.*) as Count_rentals
    FROM staff s
    JOIN rental r
      ON r.staff_id = s.staff_id

  GROUP BY 1,2,3
  ORDER BY 4 DESC;


****************************
*SLIDE 4                   *
****************************
  SELECT sub.pay_mon, 
         sub.fullname, 
         sub.counter as pay_countpermon, 
         sub.amount
  FROM
         (SELECT 
                 CONCAT(c.first_name, ' ', c.last_name) as fullname,
                 DATE_TRUNC('month',p.payment_date) as pay_mon, 
                 COUNT(p.rental_id) as counter, SUM(amount) as amount
            FROM payment p
            JOIN customer c
              ON c.customer_id = p.customer_id
           WHERE DATE_TRUNC('year', p.payment_date) >= '2007-01-01'
      
          GROUP BY 2, 1
          ORDER BY 1, 2
         ) sub
  JOIN 
         (SELECT 
                 CONCAT(c.first_name, ' ', c.last_name) as fullname,
                 SUM(amount) AS amount
            FROM customer c
            JOIN payment p 
              ON c.customer_id = p.customer_id
      
         GROUP BY 1
         ORDER BY 2 DESC
         LIMIT 10
         ) sub2
      
    ON sub.fullname = sub2.fullname

{{< /highlight >}} 





**Objective 2: Python, Beginner to Intermediate**







The second objective of the course was to take Python from beginner through intermediate.  We covered the value proposition of Python (great for data, great for big data, great for sorting, great for analysis), syntax, and Pandas and Numpy libraries.  The capstone project for Python was outstanding.  We created a full blown application for reading Bike Share data from three cities: Chicago, Washington, and New York City.  The data was already cleaned and well structured.  Total transactions were about 1 million, give or take.







**Python Capstone Project**





![](/images/Peek-2020-05-13-10-38.gif)
A walk through of the data analysis of the Bikeshare program.





**Python Code**







I've also uploaded the code to [GitHub](https://gist.github.com/kylepott/c21585fc50d9951766c7bcb290c39689) if you'd like to fork the project.



**Objective 3, Terminal + GitHub**







The final technical objective of the course was how to use the UNIX/Linux Terminal and GitHub.  As a 14 year daily Ubuntu Linux user there wasn't much new or me in this portion, but still a good quick refresher.

{{< gist kylepott c21585fc50d9951766c7bcb290c39689 >}}



**Putting It All Together**







As courses like this go, I think the best learning comes in the form of the capstone projects, applying the skills in our day jobs, and using the skills to tackle personal projects.  I won't recap these in depth, but I very much enjoyed putting my new skills to use on several personal projects:





  * [Machine Learning to Transform Photos into 3D with Python](https://technicalagain.com/2020/05/11/machine-learning-transforming-photos-into-3d-with-python/). _Using an AWS GPU instances to run PyTorch to create 3D images. CloudWatch implementation to control costs._  * [Build a Multiplayer Online Game in Python](https://technicalagain.com/2020/05/07/building-a-multiplayer-online-game-in-python/) _Online game that can be played by up to 10 players. Client and Server architecture written totally in Python._



  * [According to Facebook, I will Have a Dad-Bod on June 28, 2021](https://technicalagain.com/2020/04/14/according-to-facebook-i-will-have-a-dad-bod-on-june-28-2021/) _A data science project that uses Python to predict future weight gain. Also, created an open source project [Dad-Bod on GitHub](https://github.com/kylepott/Dad-Bod)._  * [Part 2: My Future Self is Beating the Dad Bod](https://technicalagain.com/2020/04/16/part-2-my-future-self-is-beating-the-dad-bod/) _I created another open source tool to send myself a daily text message tracking my progress to goal._



  * [Using Data Science to Pick NCAA Tournament First Round Winners](https://technicalagain.com/2020/03/07/using-data-science-to-pick-ncaa-tournament-first-round-winners/). _Using correlation to find the variables that are most predictive of NCAA men’s basketball first round tournament wins._  * [Building a Model to Pick NCAA First Round Winners](https://technicalagain.com/2020/03/15/building-a-model-to-pick-ncaa-first-round-winners/). _Part two of my previous post that builds a data science model to predict NCAA tournament winners._













