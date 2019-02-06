# Day 2 lab
## Purpose
We will use a new database called **world** and run simple ```SELECT``` queries (Unit 2.0-2.5) on it.
## What to Do
To complete your lab, open a *new* text file in your text editor (Use BBEdit, Sublime or Notepad, **NOT** Word, TextEdit, or Google Docs - we don't want any "smart" quotes or rich text formatting) to type your answers to today's lab questions:
1. Write the SQL to show what is the life expectancy for Afghanistan. Show the country name and the life expectancy.
1. Write the SQL to show the country names and life expectancies for all countries with life expectancies below age 50. 
1. Show countries and the year that they became independent. Exclude any country with a ```NULL``` value for independence.
1. What about the countries that never became independent (where IndepYear ```IS NULL```)? Write a query to show the country name, the fact that their independence year is null, the form of government and who the ruler is.
1. Sometimes it is tricky to deal with single quotes in data values. Special care must be taken with quotation marks. Write a query to find any data values in the HeadOfState column of the Country table that have a single quote in them. Write the query and give the name of the country (if any) in your answer.
1. Write the SQL to show all known information about cities. (do not use the LIMIT keyword) You do not need to show the answers, just the SQL.
1. Write the SQL to show the population and city name for the city called Kabul. 
1. Write the SQL to show the population and city name for both Kabul and Qandahar. 
1. Write the SQL to show the population, country code, and city name for all cities in Afghanistan (use country code AFG). 
1. Suppose we are interested in extreme minority official languages. These are official languages that are officially sanctioned by the government but have less than 10% of the population speaking them. Write a SQL query to show the language, the country code, and the percentage. Only show official languages.
1. CHALLENGE: How old is this data? How can you use the data values themselves to reveal the age of the data set? (Hint: who is the US president?) Can you write a query to help prove your hypothesis about the age of the data?
## What to Turn In
* Paste in your SQL answers in the ```Day2``` lab assignment area on Moodle. (You may also create a text file of the answers if you'd like to save it for your own use.)
* Turn in as much as you were able to do. 
* You can finish the rest on your own time so that you stay in sync with the rest of the class.
