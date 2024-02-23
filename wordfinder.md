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

In the HTML game page we used a collection of divs modified with CSS to create the grid structure. Each div was assigned an ID so we could register which square of the grid was clicked on and use this information to build words. We used javascript to handle filling the grid with the randomly selected letters as well as to handle when the user clicked on a specific square of the grid. When a user clicks on a square the program registers the ID of which box was clicked and stores it in an array, it also registers the letter contained in the square and concatenates it to a string. As the user clicks valid squares in the grid each ID value is added to the array of IDs and each letter is concatenated to the string. A valid click means that the player can only click on squares that are touching the previously selected square. If they attempt to click a previously selected square or one that is not touching nothing will happen. When the user thinnks they found a word they then click the submit button. This takes the string that was created and sends it to a server side function to handle checking the validity of the submitted word. 
To determine the validity of a selected word we decided to utilize the Merriam Webster Dictionary API. We would send the word the user created to the API and if it came back as an actual word we would score it depending on how many letters it contained. If the API sent back a response saying it could not find the word, we informed the user that the word did not exist.

My contributions to this project included writing the functions that filled the game grid with letters, various functions that handled the user clicks on the grid, and the functions that handled randomly selecting letters for populating the game board. 

To fill the grid with letters I took the array of letters that was randomly generated server side using C# and placed them in each square of the grid.

![fillgrid](https://user-images.githubusercontent.com/84057490/184509031-c4de976c-4922-437b-91d9-346fd134d01c.png)

To handle the user selections I created an on click function that would register the id and letter of the square clicked. The function would check to see if the click  was the first square they had selected or not. If so then it would store the id and letter in the array and string appropriately and change the color of the square to green to show that it had been selected. If it was not the first square the user had selected, a second function would be called that would check the validity of the click. To do this I first had the function check the array of saved IDs to make sure that it was not a previously selected square. If it wasnt it would then check to see if the selected square was touching the previously selected square. To accomplish this I made a array of arrays that essentially acted as a key for each square. The function would take the ID of the currently selected square and send it to the jagged array. Then depending on the ID sent to the jagged array, there were inner arrays that contained elements holding the values of what squares were valid depending on the ID (I hope that this made sense because I had a difficult time trying to figure out how to explain it). If both of the checks failed then the uer click would do nothing.

![vars](https://user-images.githubusercontent.com/84057490/184509440-d13d5385-1896-4584-b455-1e214c46427b.png) ![onclick](https://user-images.githubusercontent.com/84057490/184509428-bcaa0308-c3ca-4e38-8452-9372e38b5ef4.png) ![checkClick](https://user-images.githubusercontent.com/84057490/184509418-eed3cdde-4f3c-40b3-8445-742099679fc1.png)

On the server side of the program I created the functions that randomly selected the letters to populate the game board with.
To accomplish this part I decided to model how we selected the letters after how the actual game of Boggle selects letters, with dice. To model the dice I created a list of arrays with each array representing one of the sixteen dice. Each array contained six elements corresponding to the different die faces. I initialized the elements with letters that were found on a set of dice from a standard English Boggle game. 

![boggledice](https://user-images.githubusercontent.com/84057490/184509565-c71ce8bb-10d5-489c-9052-166bf11085f7.png)

To populate the board I wrote a simple function with a for loop that would iterate through each element of the array used to simulate the boggle board and "roll" one of the dice held in the die list. This rolling of the die was handled by another function that would use a random number generator to select a die(array) from the list and then randomly select a face from that die. The function would then remove the 'rolled' die from the list so that it could not be selected again.

![dicefunction](https://user-images.githubusercontent.com/84057490/184509670-65dcdb7a-07da-4fa9-ad90-6fd5db52d763.png)


We encountered a few issues with getting SignalR to work correctly for both players but most issues were minor and easily fixed. One of the bigger issues we ran into was that each player was getting a different game board than the other player. To fix this we just made sure to store the values from first board that was created and pass it over to the second player so they were new creating a whole new board and instead just using the same one created for the first player. The other problem we ran into was when we tried to create a new game button. The issue was that the static variables for each player were still persisting and when a player started a new game instead of becoming player 1 or 2, they would now become player 3 or 4. This caused a number of issues such as players not being able to enter the game because the program thought the game already had two players, or if the game did start it would not keep track of words or scores. To solve this we just made sure that when a new game button was clicked both players were taken back to the start page and their connection to the SignalR chat hub was disconnected, that way when they started a new game they also initiated a new connection to the SignalR chathub with clean variables.

### Below are some screenshots from an active game session
![gameplay](https://user-images.githubusercontent.com/84057490/184510183-a6297a14-2a36-45ab-b4b5-ab0233dd27f6.png)

![game end](https://user-images.githubusercontent.com/84057490/184510188-d2d79742-2fe5-4df7-b524-81ad734b3353.png)

### [Go To Code Repo](https://github.com/aricglanville/WordFinderGame.git)
