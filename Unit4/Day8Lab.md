# Day 8 Lab: Interesting Joins and Subqueries
# Goal
Practice writing subqueries and joins.

## Questions using the 'world' database
![ERD for world](https://github.com/megansquire/CSC301Spr2019/blob/master/images/worldERD.png)

1. Using the *world* database, write a query to display the Continent, Country Name, and Surface Area for the country on each continent that has the highest Surface Area. [Hint](https://stackoverflow.com/a/1813766) that uses a "self join" - notice two the tables are joined to themselves! If you use this hint, be sure to really think about why it works. Read the SO post and try to figure out why this works.

Sample answer:

![sample answer for q2](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day8lab.2.png)

## Questions using the 'employees' database
![ERD for employees](https://github.com/megansquire/CSC301Spr2019/blob/master/images/employeesERD.png)

2. Using the *employees* database, write a query to display the employee number, first name, last name, and maximum salary for everyone with the last name 'Facello,' but only include those who make more money than the person named 'Georgi Facello'. Do not assume you know Georgi's employee number in your final query. (Your query should only use his name.) Your query will return 24 rows.

Sample answer

![sample answer for q3](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day8lab.3.png)

## Questions using the 'wine' database

ERD for the wine database

![ERD for wine](https://github.com/megansquire/CSC301Spr2019/blob/master/images/wineERD.png)

3. List all the countries in the wine database, and the count of customers that have that country listed. If there are no customers from that country, you don't need to list it. Hint: perform a "sanity check" on this result and make sure it is accurate! :) This question can also be solved with a NATURAL JOIN if you'd like to try that out.

4. List all countries (country id and country name), and their customer counts, but be sure to list the country even if their customer count is 0.

5. Using the *wine* database, write a query with a subquery to display the wine_id, wine_name, year, and cost for the most expensive wine(s) in the inventory. When writing your query, do not assume you already know the price of your most expensive wine. DO NOT USE A LIMIT.

Sample answer:

![sample answer for q1](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day8lab.1.png)

In addition to using the subquery, can you also use the technique from \#1 above to answer this?

# What to turn in
Turn in to Moodle a text file with your answers to as many of these 5 questions as possible.
