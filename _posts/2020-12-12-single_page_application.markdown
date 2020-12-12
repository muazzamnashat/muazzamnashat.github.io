---
layout: post
title:      "Single Page Application"
date:       2020-12-12 11:18:51 +0000
permalink:  single_page_application
---


For my JavaScript project at Flatiron School, I made a *Single Page Application (SPA)*, **Yap**, which helps users view, create and read reviews about different restaurants around the world. Review is something I really care about before going to a new place particularly during an unprecedented time, when most of the restaurants are closed for dining in and you have to make takeout orders. You want to make sure you order the right food. This app help users find restaurants with google search and write reviews or write review if this restaurant is already present in the app. Yap uses Rails on backend and vanilla JavaScript on frontend.

The hardest part of the project was to get my head around the idea of SPA! I was used to the idea of having multiple HTML files and rendering them with rails. But, when I learnt that I have to build a complete SPA with pure JavaScript, I was literally banging my head against a wall thinking how I can have multiple pages within one page! However, I decided to start with the backend first and made sure my API was working as expected before starting with the frontend. As soon as I started with the frontend, I quicky realized the power of JavaScript and its power to manipulate the DOM. Gradually every piece was coming together. 

However, another challenge was building a search button. I wanted to build a search button where users can type names and suggested results will keep popping up as they type. The function looks like this: 

![Code](https://github.com/muazzamnashat/yap-backend/blob/master/carbon%20(1).png)

Here, when the user type something on the search bar and the string is at least 3 character long, the frontend fires an API call and get all the restaurant list. Then, if the string matches with any restaurant name then that restaurant object is saved in an array. Then, another function is called to populate the result div. Although this might not be the most efficient search system as it keeps calling the API with every input but for the purpose of this small project, I did not spend much time on this feature. 

The purpose of this project was to get students familiar with DOM manipulation with pure JavaScript. Although there are libraries in JS like React, to make things easier for developers, but before getting used to these libraries it was essential to understand how JS works with the DOM. The app definitely helped me understand JS better. 


