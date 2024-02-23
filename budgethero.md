<!--
layout: page
title: "Hangman Game"
permalink: https://aricglanville.github.io/banking 
-->

## Capstone Project - Budgeting app

For this capstone project I worked with a team of three others to develop a household budgeting application that was focused toward college students sharing housing. We wanted to implement a slightly different system than other similar applications currently on the market by allowing members within a household to share bills either based on income percentage or a specific value amount. To maintain data fidelity between instances of the application which would allow easier sharing of household info between users as well as allow users to login on different machines, we created an API that allowed us to store and pull our data from a cloud hosted database.

For the technologies we used in our project we opted to develop using an MVVM design pattern with the following tools:
1. IDE - Visual Studio
2. Repository – GitHub (program code and documentation)
3. Project Coordination and Bug Tracking - Trello
4. ORM Framework - Entity Framework
5. Languages - Backend: C# .Net6 , Frontend: Xaml
6. UI Library - WinUI 3
7. Server VM for API – Linode
8. API Framework – ASP.NET
9. Database – SQLite
11. API Testing - Postman
12. Team Collaboration - Discord

The way that the app works is each user of the program has an individual login that accesses their personal budget profile where they can manage bank accounts, transactions, budget items, and produce reports, with all of these items only visible to that specific user.
Within their personal user dashboard they can also elect to create a household. When creating a household, the creator is able to invite other users of the budget application to join their household by giving them a unique join code to enter from their dashboard. Once a household has been created, hosuehold members will then be able to add bills/transactions that are shared among all members of the household. When creating a shared bill, the user is able to specify which household members will be included on that bill and whether the bill will be split based on the difference of each members income percentage or by a specific amount. After the bill creation has been completed, the bill will show up in the shared household tab that all members have access to. In this household tab each user can see the total amount of the bill and whether or not a member has paid their portion of it (they will not be able to see how much that member paid though). Along with this, each household member will also have a budget category created in their own private budget page containing all of the bill items reflecting the amount they owe. To pay towards a bill, the user will simply create an transaction, selecting that bill from the category drop down, and allocating funds from their selected bank account. This will reflect on the bill item in their personal budget page as well as the shared household page.   

Within each users personal dashboard there are a few tabs for different types of budget tracking they can perform.
- On the bank account page they can create different bank accounts for tracking balances. Having a bank account with funds also allows the user to allocate funds to transactions.
- On the users personal budget page, users can add category groups for their budget. Once a category group is added they can then edit those category groups to add, edit or remove budget items within that specific category. When adding an item to a group the user can name the item and set a budget amount for it. After this item is created, the user will then have the option of selecting it from a dropdown when creating a transaction. The users personal budget page is also where their individual portions of household bills will show up.
- On the transactions page, users can add either an expense or deposit transaction. When adding transactions the user will add the payee and amount along with selecting a bank account to allocate funds from and a category in the budget to add it to.


On this project I worked as the product owner since the idea was mostly mine. Along with this I determined how the UI would work and what the system requirements would be, as well as developed most of the UML diagrams and database schemas we would use. As far as my coding responsibilites go: I developed a good portion of the UI for the main dashboard along with a couple of the forms; I coded all of the logic for the budget and household pages including their associated forms; I created the data models we used for data management.

By the end of the semester we were able to get 95% of our project completed and working amazingly. One of the things we did not end up having time to finish was the income tracking system that would allow users to split bills by difference of income percentages.


### _Code Repos_

This first repo contains the last instance of code that compiles and executes with a majority of the app functionality. What doesn't work in the repo is the API because the connections weren't complete at this point, the household page (because the API connections arent complete), the reports page, and the detail panes of each dashboard tab. I am including this repo because it is at least a good example of how the base functionality of the application works.
## [BudgetHero Working version](https://github.com/aricglanville/Capstone-BudgetHero.git)


This second repo is our completed project with the API code finished as well as the household page, the reports page, and the detail panes. The unfortunate thing is that this code will not get past the login screen because our database is no longer being hosted and the API commands go nowhere, however, this is still a great code representation of our finished product.
## [BudgetHero Final Version](https://github.com/aricglanville/Capstone-BudgetHero-Final.git)
