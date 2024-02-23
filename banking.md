<!--
layout: page
title: "Hangman Game"
permalink: https://aricglanville.github.io/banking 
-->

## Banking App

This project was to create a simple banking app with the following requirements:
1. Use a login system that allows account creation, verification of credentials, and password hashing.
2. Allow the user deposit/store/withdraw money into three accounts.  Transfers are done within a user's accounts, and not to other user's accounts.
3. Show both a full account transaction history and an individual account transaction history, with date times and money changes. 
4. Utilize .NET on the server end.
5. Utilize an SQL database to store user information.

To create our project we used the ASP.NET MVC Framework and MSSQL for the database application.

For the login system we used the register and login scaffolding included as part of the ASP.NET Core Identity API to satisfy the first requirement. Its included functionality handled all of the account creation including password hashing, and user authentication.

After the user logs into their account (or creates a new one) they are shown their account dashboard. This dashboard shows the current balances of their checking, savings, and loan accounts. There are modal buttons on the left hand side that allow the user to transfer money between their own accounts, or deposit/withdraw from those accounts as well. The user also has the ability to check their full transaction history by clicking the button underneath their account balances, or they can view the transaction history for each individual account by clicking the account names. One of the biggest issues we ran into was how the program was saving transactions. When a user initiates a deposit/withdraw transaction, one transaction record is created showing the account affected, the amount transacted, type of transaction and a date stamp. This part of the program worked fine, however, the transfer transaction function was causing issues. If working correctly a transfer should create two transaction records reflecting each account involved in the transaction. The issue we were having was that instead of two seperate records being created, one for each account, the first account's record was being duplicated and no record for the second account was being created. We recognized that the problem was stemming from trying to use the same Transaction object for both transactions. For some reason the data members in the Transaction object were not being overwritten when the second transaction took place. To fix this we simply created a second Transaction object to hold the second transactions information and then store it in the database.

### Example of a users account dashboard
![accountDash](https://user-images.githubusercontent.com/84057490/184463038-712c6e1e-d89a-48b0-9795-dfac47815296.png)

### Full transaction history page
![fullTransHistory](https://user-images.githubusercontent.com/84057490/184463058-d671ea87-570d-4a35-9dfb-b89ea8af60f3.png)

### Deposit/Withdraw Modal
![depositModal](https://user-images.githubusercontent.com/84057490/184463120-67a25b10-ec86-45fe-980c-4dc27f95728f.png)

For my part of the project I worked on a portion of the HTML for the dashboard page, specifically the section that displayed the account balances. This was a little tricky for me at first because this project was my first time using the MVC Framework and I still didn't fully understand how a lot of it worked. My biggest problem was that I just did not know how to pull information from the database to reflect on the webpage. Luckily, one of my team members had a decent amount of experience with it and was able to show me the issues I was running into and how to solve them.

### HTML For the Account Balances Display
![acctBal](https://user-images.githubusercontent.com/84057490/184463412-a9c6c07e-b34c-46d8-9233-8bd3e812dd66.png)

I was also responsible for writing the code that handled the deposit, withdraw, and transfer account functions. For this I just had to make sure that I was correctly capturing which accounts were being accessed and that the amounts affecting those accounts were being handled properly. For example, with transferring, I had to ensure that the amount was being converted to pennies then being added and subtracted to/from the correct accounts. This also meant making sure that if one of the accounts was a loan account, then the inverse operations were being applied. The reason for this is because if you are withdrawing money from a loan you are actually increasing its balance and if you are depositing you are lowering the balance by paying it down.

### Function That Handles Transferring Between Accounts
![image](https://user-images.githubusercontent.com/84057490/184463699-8ec74ca4-e396-478f-a1db-5f78fcfcb897.png)


Lastly, since we were representing all of the account balances in the database as pennies I wrote some functions that would convert the penny amounts to decimal amount and vice versa.

### Conversion Functions
![conversionFuncs](https://user-images.githubusercontent.com/84057490/184463725-b23f6c88-2deb-41c0-82f1-0d7a566eb03e.png)

### [Go To Code Repo](https://github.com/aricglanville/BankingApp.git)
