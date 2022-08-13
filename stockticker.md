<!--
layout: page
title: "Stock Ticker Game"
permalink: https://aricglanville.github.io/stockticker
-->

## Stock Ticker Game

For this group project the assignment was to create a game that simulated investing in the stock market using .Net Core and asynchronous communication. Once the game started we were not allowed to refresh the page, or forward/redirect to a new URL, all data sent to and from the server had to use eithe AJAX or Web Sockets. To handle the asynchronous communication we decided to use AJAX to send and request data to update the stock prices.

To start the game we were required to have the user choose a stock ticker symbol. We decided to use a drop down list to containing 6 of the more popular stocks so they could have a predefined list to choose from. The reasoning behind this was because we thought some people might not exactly know specific stock symbols for the companies they are interested in and this would prevent a lot of trial and error type guessing, or spending extra time having to google the correct ticker symbols.

After the user chooses a symbol, the game starts and they are given $10,000 to begin investing with. Also, a day of the week more than six monts old is chosen at random and the user is shown the opening value of the stock they chose for that specific day. The user then has the option to buy or sell stock, or hold and do nothing. If the user decides to buy or sell they are able to use either a slider or a text box to enter the amount and submit. If they decide to hold, nothing happens and the game progresses to the next week. This gameplay loop continues until the user decides to quit by clicking the "Quit" button, or the game date surpasses the current day. We decided to progress the game in weekly intervals so there would possibly be larger changes between opening stock prices shown to the user. When the game ends or the user quits voluntarily all stocks that the user owns are automatically sold at the current price and added to their bank account. They are then shown the current amount of money in their account. 

For my part of the assignment I handled writing most of the functions, this included using C# for server side functions and Javascript for the client side functions. In C# I wrote a few functions that helped with gameplay logic, this included a function to progress the gameplay, a function to find a random day to start on, and a function that 


This was definitely a difficult assignment and we did run into a few problems along the way. The first problem we ran into was 


[Go To Code Repo](https://github.com/aricglanville/StockTickerGame.git)
