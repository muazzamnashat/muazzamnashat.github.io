---
layout: post
title:      "My first project at Flatiron School – Job Search CLI program! "
date:       2020-09-12 02:50:18 -0400
permalink:  my_first_project_at_flatiron_school_job_search_cli_program
---


Before joining Flatiron school, I was looking for jobs and I won’t lie I had applied to a ton of places! I went to LinkedIn, Indeed, Glassdoor, and whatnot. This was a terrible experience! Now, as I am heading towards a Software Engineering career (always feels exciting to be picturing myself as a Software Engineer!), I was wondering if there could be a one-stop solution that would help software engineers find their dream jobs easily. This CLI program ‘Job Search’ is the very beginning of my dream project! 

Job Search CLI uses the GitHub Jobs API and shows software engineering jobs according to the user preferred location and programming language. First, it prints a list of available job locations depending on the currently active job listings on GitHub. Users can choose a location and then it will show a list of programming languages mentioned on those job listings. Users can select any programming language and it will show the job listings without the job descriptions. Job descriptions are deliberately hidden from the list because it will make the printout looks messy. But users can select a job number to read the description. However, users has option to exit the program anytime.

At Flatiron school, for the last couple of weeks, I have been learning Object-Oriented Programming (OOP) in Ruby. For most of the labs, the instructions would give hints at what classes were needed and how they would interact. I solved the labs but did not comprehend the true beauty of OOP until I used OOP to build a program from scratch. 

This program uses three classes. The API class is responsible for fetching API data and creating Job instances using the Job class. CLI class is responsible for the functionality of the program. Putting together the program and making it print something was fairly an easy task. The hardest part was considering the edge cases, in other words, improving the user experience. For example, if there’s a typo, the users would not get any error message or a chance to re-enter the input. But the hardest part was when a user would select a location and a language but there was no match for that. The program would skip that function and keep printing the next messages. I had to code another method and re-write some other methods to tackle this problem!

Although this is a very simple CLI program, this taught me a lot. I have learnt how to design a program, make objects that interact with one another, use an API to show data to users and most importantly embracing failures that will come along with coding.

