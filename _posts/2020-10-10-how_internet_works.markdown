---
layout: post
title:      "How internet works!"
date:       2020-10-11 02:35:02 +0000
permalink:  how_internet_works
---


You would never be able to appreciate the efforts engineers put in to build services that make our lives easy until you build one by yourself. It might seem trivial that we click on a button and something shows up, maybe it's our Facebook posts, bank accounts, or even a uber ride but the work that engineers put in to make it happen is enormous! Creating a web app from scratch made me realize how internet works and how complicated it is to add a functionality that enhance user experience.
 

For the last couple of weeks, I have been learning SQL, HTTP routes, Dynamic URL Routes, and how to use Ruby with a lightweight framework, Sinatra, to quickly build a web app. Using this knowledge, I have built a Stock Tracker app, a web app that let users add stocks to their watchlists. Users can follow stock news and see recommendations on the stocks they are following from stock analysts. 

The main focus of the project was building a web app quickly with CRUD (CREATE, READ, UPDATE or DELETE) functionality and user authentication. I have used Finnhub API (https://finnhub.io/) on the backend and basic HTML and CSS for front-end as front end was not the point of interest for this project! 

The features of this projects are:

•	User authentication (Signup / Login).
•	Uniqueness of user login attribute (username or email).
•	Validation of user input so bad data cannot be persisted to the database.
•	CRUD functionality.
•	Minimal design.
•	Latest news on stocks.
•	Stock analysts' recommendation on stocks that user follow with some graphs.

![](https://github.com/muazzamnashat/stocktracker/blob/main/public/for%20blog.png)

The most difficult part was planning the association between different classes and tables. Initially, I created 3 tables: Users, Stocks and a join table. My initial idea was that if I could share one stock instance between several users then I would not need to create same stock instance several times for several users. It will save memory. I had an MVP (Minimum Viable Product) ready pretty quickly and so started stretching features. I implemented a feature called ‘Note’ where users can stick notes to stocks. It would help them to plan when to buy or sell a stock. The feature was easy to implement but when I was testing the app, I realized that a user could change the note created by another user because there was only one stock with the specific name and several users could own that one stock! So, I kept only two table and allowed User class to have several stocks with the same name! Another tricky part was creating pie charts with stock recommendations but thanks to Finnhub API for their awesome documentation and easy to use API.

I have learned quite a few things from this project. First, it is really important to plan your project and have a well written steps to achieve the final project. Also, before implementing a feature, instead of just starting to code, it is really essential to write down what changes this feature will bring to your current state of the product and how you plan on handling this change in your code. Although this is a fairly small application, but I believe this lesson will help me create bigger application in the future. Further, I have learned how the internet works and how routes are used to handle requests from client. Finally, I have learned to appreciate the efforts software engineers are putting in to create apps that serves people and to enhance the user experience. Kudos to every software engineers in this world!

