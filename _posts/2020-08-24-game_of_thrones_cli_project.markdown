---
layout: post
title:      "Game of Thrones CLI Project"
date:       2020-08-25 01:44:07 +0000
permalink:  game_of_thrones_cli_project
---


My first project for Flatiron was to build a CLI by pulling information from either an API or by scrapping a website.  I am a Game of Thrones fan but admittedly have not read the books so I created this CLI which pulls from A Song of Ice and Fire (or GOT) books API so I could learn more about the books. 

As this was my first project, the most intimidating part was the thought of starting the project from scratch.  Once I laid out the steps I was going to follow it was easier to wrap my head around the project as a whole.  Now that I've gone through this process once, I believe that the flow and cadence that I used here will be helpful in my other projects going forward.  

My initial step was to work on a notes file- this file helped me scope out the project and describe how I wanted the app to function.  This file can be edited and adjusted while you're working through the project.  My next step was building a working version of the app using fake data.  I started building this version in my executable file and then moved this to its own class where I continued using fake data but made sure the objects were corresponding and functioning correctly.

Once I had a more robust version of the app, I began to pull real data from the API.  For my project this was pulling data from A Song of Ice and Fire API that I chose.  After real data is entered, it gives you more visibility into what can be refactored within your CLI, so you can work on making your code ‘DRY’ at this point. Additionally I introduced a few techniques that I felt helped the overall user experience. I installed the colorize Gem which makes the prompts and data within the terminal more readable and distinguishable. I also used the system(‘clear’) command after specific user inputs to help the readability of the app which made each prompt appear cleaner and less cluttered.  I defined a method using sleep() that lets the user know the app has received the input and their information is on the way!

What helped me the most in this process was that I consistently had a working project throughout.  I was able to build the project step by step but continuously saw it coming to life.  From a learning standpoint this was also super helpful just to watch it evolve over a few days.  This process also helped making structural decisions for the different classes easier.  Overall, the way this layout guided me was ideal for my first project.



The final version of my CLI allows you to:
* View a list of books
* Choose a book you want information on by typing the corresponding number
* Select from a menu of options the attribute(s) you want to learn about
* Go back to your list of books and options to choose from
* Exit the program
