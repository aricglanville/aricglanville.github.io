<!--
layout: page
title: "Word Finder Game"
permalink: https://aricglanville.github.io/wordfinder
-->

## Word Finder Game

This was the final, and in my opinion, the most fun project for the course. 
For this assignment we were tasked with creating a word finder game similar to the classic game Boggle.

For this assignment we were required to allow two players to play against each other asynchronously using SignalR. Along with this, the game also had to be playable on a desktop web browser as well as a mobile web browser.
Other requirements stated that we also had to make sure that both players were seeing the same grid of letters to choose from, that each player could see both players scores change dynamically as they found words, words submitted should be compared server side against a list of valid dictionary words before being scored, each word had to be at least 3 letters long, the grid of letters should be created so that vowels had a 40% chance of being generated, duplicate words could not be submitted, and when a game is over (after 1 minute) a results screen is displayed showing a list of the words each player found as well as that players total score.

In the HTML game page we used a collection of divs modified with CSS to create the grid structure. Each div was assigned an ID so we could register which square of the grid was clicked on and use this information to build words. We used javascript to handle filling the grid with the randomly selected letters as well as to handle when the user clicked on a specific square of the grid. When a user clicks on a square the program registers the ID of which box was clicked and stores it in an array, it also registers the letter contained in the square and concatenates it to a string. As the user clicks valid squares in the grid each ID value is added to the array of IDs and each letter is concatenated to the string. A valid click means that the player can only click on squares that are touching the previously selected square. If they attempt to click a previously selected square or one that is not touching nothing will happen. When the user thinnks they found a word they then click the submit button. This takes the string that was created and sends it to a server side function to handle checking the validity of the submitted word. We also implemented a timer on the client side which automatically ends the game after 1 minute is up.




[Go To Code Repo](https://github.com/aricglanville/WordFinderGame.git)
