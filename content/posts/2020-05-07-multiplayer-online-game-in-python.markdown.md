---
author: kylepott
date: 2020-05-07 01:11:33+00:00
draft: false
title: Multiplayer Online Game in Python
type: post
url: /2020/05/07/multiplayer-online-game-in-python/
categories:
- python
tags:
- game
- python
---




![](https://technicalagain.com/wp-content/uploads/2020/05/Screenshot-from-2020-05-06-16-55-30.png)
Slide 5 or 6 Nimmit! can be played with an actual card deck





![](https://technicalagain.com/wp-content/uploads/2020/05/Peek-2020-05-06-20-09.gif)
My clone of Slide 5 written in Python





I almost gave up and quit on this project.  I'm so glad I stuck with it because the results were so worth it.







After playing the **Slide 5** card game I thought it would be a great game to clone into an online game that can be played with friends over Zoom during the pandemic lock in.







The game is called Slide 5, it's a copy of the original game [6 Nimmit](https://en.wikipedia.org/wiki/6_Nimmt!) created in 1994!  If you've never played before it's really simple:  Everyone gets 10 cards and then you have to play the next lowest card.  Four rows build sequentially and if you lay the sixth card in a row or if you have a card lower than the last card in each row, you have to clear that row and take all the points.





![](https://technicalagain.com/wp-content/uploads/2020/05/Screenshot-from-2020-05-06-16-58-12.png)
My clone of 6 Nimmit! known as Six Minute.





**How I Learned**







I am in the final stages of completing a Udacity course on [Python for Data Science](https://www.udacity.com/course/programming-for-data-science-nanodegree--nd104).  The course has been great.  After completing the two main assignments for the course, I was looking for an opportunity to apply my new skills to a personal project.  I watched this two hour seminar from freeCodeCamp [Python Online Multiplayer Game Development Tutorial](https://www.freecodecamp.org/news/python-online-multiplayer-game-development-tutorial/) and decided 6 Nimmit! was the perfect game to code.







I felt especially motivated to apply my skills after reading a number of posts on reddit  about people caught in [Tutorial Hell](https://www.google.com/search?q=reddit+tutorial+hell&oq=reddit+tutorial+hell&aqs=chrome..69i57j35i39j69i60.7909j0j4&sourceid=chrome&ie=UTF-8) and wondering if I, myself, was trapped in Tutorial Hell without knowing it.







**What I Learned**







The whole project is [available on GitHub](https://github.com/kylepott/six-min).  Like all my code on GitHub, it could stand a good refactoring so try not to judge me too harshly on the repetitive code or the somewhat cryptic aspects that could use a good commenting.  Here is what I learned, in brief:





  * How to build a server   * How to connect clients to the server  * How to store and retrieve objects on the server (Python Pickle package)  * In depth understanding of the Pandas and Python data structures: dataframes, dictionaries, lists, tuples, series, and strings  * In depth understanding of how to search and sort data structures  * How to manage queuing the clients (everyone must be playing in the same round)  * Game programming concepts: actions, penalties, scorekeeping.  I think I could program another game with a different concept much quicker just because I have a framework for how to implement the major aspects of any game - the game "story arc" if you will.  * I did a good job with continuous integration, and building and deploying working code.  Every time I touched the project I completed the night with working code checked back into git.  Little by little, I chipped away until I was totally done.





**What I Struggled With**







Lots.  Let me just start with that.  There were several moments that I was within an inch of quitting and got really down on myself.  Here were some of the toughest challenges:





  * The very first data exchange between the server and clients took me a full night to get right.  * Port management is not implemented very well.  When the program ends, sometimes the operating system thinks the port is still in-use.  * Keeping the clients in sync.  For example, if one of the players got penalty points, only one client should update the scoreboard - not every client.    * Data structure sorting.  This was one of the most complex aspects of this game because so much has to be sorted: the game board, each player's hand, the rounds, and the scoreboard.  Additionally, the scoreboard is interwoven into the game interface.  If you look at the image up above you see in my hand that the 11 is worth five points and 75 and 95 are each worth two.  That was tricky to implement well in the terminal.  * Controlling the use of random function on the server.  While the server creates the gameboard and each player's hand by creating a random numpy array and "popping" cards out of the deck into the hand, each client can't receive a random hand or a random gameboard or we have pandemonium.  * Obviously, I did not implement a traditional user interface.  * The server does not have session management.  If I kept going, I'd build a way to run multiple games simultaneously and keep track of which client is playing which game.  * My testing and debugging practices are pretty rudimentary.  It would be good continued learning to use pytest and improve my automated code coverage skills.  * I have not deployed the app to the web.  So another area for development would be to deploy in flask or django or deploy serverless on AWS, etc.  Challenges for another day, I suppose





**Would I Recommend this Project?**







I would recommend a project like this to an intermediate programmer who has previous experience developing a complete application.  This project really helped me level up my skills.  I grew tremendously by sticking with it and getting done.  However, there was a lot of frustrating nuance in this exercise.







Here's one unexpected drawback of creating a game.  After all the hours I poured into building the game and the increasing complexity in debugging and testing the game, I'm so sick of it I hardly want to play it.  I hardly want to write this blog post about it.  Hopefully, I'll be up for the challenge because we're hosting a family "game night" on Zoom on Sunday where we will play the game.









