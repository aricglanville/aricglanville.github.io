<!--
layout: page
title: "Hangman Game"
permalink: https://aricglanville.github.io/hangman
-->

# Hangman Game

This was the first project assigned in my CS3750 course and the only non-group project for the course.
The task was to design a hangman game that used PHP to handle server side programming and logic.
The website for the game is hosted on infinityfree.net and uses their MySQL database tool to manage user info.

The assignment itself was comprised of three requirements: the login system, the game logic, and a high scores page.

For the login requirement I needed to allow the user to create a new account or sign in with an existing account. The username had to be unique and the password needed to be hashed. To store new user info into the database and retrieve existing user info I used MySQL prepared statements to prevent SQL injection. For new users, I had to first ensure that their chosen username was not already in use. After that, the program then creates a random 4 integer salt and appends it to their supplied password request. I then use the SHA-256 algorithm to hash the salted password before storing it and the salt in the database. For existing users I just needed to make sure that the supplied username exists and then take the supplied password and append the salt stored in the database under that username to it, hash it, then compare it to the stored hashed password/salt combo.


### This is a part of the code that handles creating a new user
![newusercode](https://user-images.githubusercontent.com/84057490/184460373-5d2a889b-b40e-41aa-ac4a-b4dd2e4a37c4.png)


The gameplay logic required that words be randomly chosen from a pre-defined list and that the word itself is never sent to the client. To do this I created a table in the database as my list of words. After the user logs in, the game initializes by selecting a word from the table randomly and storing it into a session char array variable. The purpose of converting the string word into a char array was to make checking for letters and displaying letters on the gameplay page easier. Every time the user enters a letter to guess, the letter is checked against the chosen word server side using PHP and MySQL prepared statements. As the player attempts to guess, the number of guesses is tracked and used for scoring. The game ends when the player either guesses the correct word or uses 12 guesses. When either of these conditions are met the game ends and a high score page is shown that displays the best top ten results for the number of letters in the word as per the assignment requirements. In the gameplay logic I also implemented some error handling to make sure the game runs smoothly, this included making sure the user only inputs a single letter and that the user doesnt repeat guesses. I also created an onscreen list of previous guesses to help the user as well as onscreen feedback based on what the user guesses.


### This is a part of the code showing part of the HTML for the main gameplay page
![gamepage](https://user-images.githubusercontent.com/84057490/184460912-6a1df465-5e6d-4a24-9652-a6cce799fc2e.png)


### Below are some screenshots of the gameplay page and the score page.
![gameplay-page](https://user-images.githubusercontent.com/84057490/184458948-e4e40b09-5417-49c9-8870-aa43349932ce.png)

![high-scores](https://user-images.githubusercontent.com/84057490/184459007-24ca9416-5a18-4a15-827d-cc3949a9a5f4.png)


[Go To Hangman Game Website](http://aric-glanville.epizy.com/welcome.html)

## [Go To Code Repo](https://github.com/aricglanville/3750HangmanGame.git)
