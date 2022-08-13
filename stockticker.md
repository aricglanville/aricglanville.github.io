<!--
layout: page
title: "Stock Ticker Game"
permalink: https://aricglanville.github.io/stockticker
-->

## Stock Ticker Game

For this group project the assignment was to create a game that simulated investing in the stock market using .Net Core and asynchronous communication. Once the game started we were not allowed to refresh the page, or forward/redirect to a new URL, all data sent to and from the server had to use eithe AJAX or Web Sockets. To handle the asynchronous communication we decided to use AJAX to send and request data to update the stock prices.

To start the game we were required to have the user choose a stock ticker symbol. We decided to use a drop down list to containing 6 of the more popular stocks so they could have a predefined list to choose from. The reasoning behind this was because we thought some people might not exactly know specific stock symbols for the companies they are interested in and this would prevent a lot of trial and error type guessing, or spending extra time having to google the correct ticker symbols.

After the user chooses a symbol, the game starts and they are given $10,000 to begin investing with. Also, a day of the week more than six monts old is chosen at random and the user is shown the opening value of the stock they chose for that specific day. The user then has the option to buy or sell stock, or hold and do nothing. If the user decides to buy or sell they are able to use either a slider or a text box to enter the amount and submit. If they decide to hold, nothing happens and the game progresses to the next week. This gameplay loop continues until the user decides to quit by clicking the "Quit" button, or the game date surpasses the current day. We decided to progress the game in weekly intervals so there would possibly be larger changes between opening stock prices shown to the user. When the game ends or the user quits voluntarily all stocks that the user owns are automatically sold at the current price and added to their bank account. They are then shown the current amount of money in their account. 

This was definitely a difficult assignment and we did run into a few problems along the way. The first problem we ran into was that the API we were using to pull stock information kept throwing errors. After watching the dates it was picking closely we were able to determine that the errors were being thrown when a date that was on a weekend got sent to the API. To fix this we just added some code in the random date function to ensure a weekend was not chosen. The next big error we ran into was that we were keeping all of our variables on the server side. The issue was that we did not realize whenever an ajax call was made from the game page and sent to the server for processing, when the server was done handling the call it would essentially reset and our variables would re-initilize losing any data we wanted to remain persistent. After a lot of back and forth of what to do to solve this, we ended up moving all of the important variables that we needed to be persistent to the client side within the javascript. This meant we also had to change the javascript functions to handle any of the variable manipulation such as calculations to the stock amount and bank balance. At this point the only things happening server side now were the API requests which was part of the assignment requirements.

For my part of the assignment I had originally written most of the ajax call functions for the client side and their counterpart OnPost functions in the c# server side. However, when we found we were having issues with the variables one of my team members took a lot of the logic that I had written on the server side and repurposed it to work on the client side in the javascript. He also had to reorganize and combine a few of the javascript functions that I wrote to handle the new system that we were implementing.

As the game sits it works for the most part. The only issue we are running into now is that the API throws a 426-Too many Requests error if a certain amount of requests are made in a specific timespan. Unfortunately this is not something I think we can fix directly because it is a built in part of the API. The only solution would be to find a better API that allows for more requests within a certain period of time.

###Script for Accept button handler myself and my team mate Cayden worked on
![acceptScript](https://user-images.githubusercontent.com/84057490/184507772-c86306cd-60be-495e-9ba6-634adda8267e.png)

###Function I created to find a random day to start the game on as well as the Ajax functions I assisted with
![image](https://user-images.githubusercontent.com/84057490/184507826-4e7f7d9a-aaba-432b-9635-6737c33f7cec.png)

###Screenshot of a game in progress
![gameplay](https://user-images.githubusercontent.com/84057490/184507898-afd6c767-23cf-480c-a466-3f116bd07e8b.png)

[Go To Code Repo](https://github.com/aricglanville/StockTickerGame.git)
