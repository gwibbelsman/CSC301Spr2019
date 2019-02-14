# Day 4 Lab
## Purpose
Practice with SQL functions introduced in Unit 3.1-3.3

## What to do
Open a text editor to create a .txt file to store your answers to the following questions.

[String functions documentation](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html)

[Date and Time functions](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html)

[Numeric functions](https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html)


### *World* database

1. Write a SQL query to list each continent (Africa, Asia, etc) in upper case, and show each region within that continent, and then count how many countries are in that region. Sort these in alphabetical order by continent and then by count. 

Hint 1: write this query in pieces and add features as you go. For example, write the group by and make sure that works, then add the uppercasing.

Hint 2: here is a screenshot of the results we want. Remember that `Continent` is an `enum` data type column. The sort order of an `enum` column is pre-specified in the table structure. If the order is not coming out how you want, remember that the screenshot below shows CAPITALIZED Continent names. Think about this: why does capitalization change the `ORDER BY` results?
![q1](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day4lab.0.png)

2. Construct a SQL query to list countries that have a country code that is the same as the first three letters of a country's name. For example, AFG = Afghanistan, and ALB = Albania. Hint: there are 76 results - only 76 countries have an abbreviation that is the SAME as the first three letters of its name. In your result, list the country name and the code.

3. Construct a SQL query that will list the countries from largest to smallest by land area. Print them so that the answer looks like the result below, in a single column. Your result will have 239 rows, one for each country.

![q3](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day4lab.1.png)

### *Employee* database

4. Congratulations, you have been assigned to the birthday party planning committee for the company in the `Employee` database. Write the SQL to print out a list showing each month of the year (numbered 1-12) and count how many people have a birthday in that month. Put these in order by month (1-12).

5. Assuming you can feed 100 people with one extra large birthday cake, how many cakes will you need each month? Make sure you *round up* so no one gets left out of the cake-fest. Write SQL to show the month number, the number of birthdays that month, the number of cakes needed, and a calculation of the total cake budget (each extra large sheet cake costs $43.) Show this number with a dollar sign and commas for the thousands places (if needed), as follows:

| Month | Birthdays | Cakes | Cake Budget| 
|-------|-----------|-------|------------|
| 1 | 25412 | 255 | $10,928.00 |

### *Music* database

6. Which state **in the United States** has the most customers? Show the state with the highest count of customers.

7. Imagine that we would eventually like to draw a graph of the number of invoices by month and year. Write the SQL that will yield the data needed to make this graph. Put the data result set in order by year and then month. Display the name of the month, but put them in the order that they appear in time (January comes before February, then March, etc. ). 

8. Imagine you are a customer service representative. You answer the phone and the person complaining on the other end says his name, and you hear him say something like "Louis" for this first name. However, you run a SQL command to search for first names like Louis and nothing comes up. Write the SQL command to find all the customer details for a selection of names that might *sound like* Louis. Hint, it should match names like Luis, Luís, Lewis and even Lucas, but without specifically naming any of those names in the query. Another hint, check the [MySQL documentation](https://dev.mysql.com/doc/refman/5.7/en/string-functions.html) for possible string functions to use...

9. On what day in history did your Music company make the most money? Write the SQL to calculate a total for each date. Format the total sales as currency, with a dollar sign and a period between the dollars and cents. Display only the information for the highest total date.

10. What day of the week do we make the most money? Write the SQL to show the days of the week (Sunday, Monday, etc) and the sum of all invoices presented on that day, ever. Can you sort the items in the order that the day appears in the week (so for example Sunday is first day, then Monday, etc)?

11. We want to find the Customers who have a Last Name that includes characters other than those found in the English alphabet. All these special characters will have a character length that is smaller than the actual length of the string in bytes. For example, the string Muñoz has only 5 characters, but the string has a length of 6, since the ñ character takes 2 bytes to store, rather than just one. Write the SQL to display the LastName, the length of the name in bytes, the length of the characters in the name in bytes, BUT only show the names where there is actually a difference between length and character length.

12. Which song (track) is the most expensive per second? Write a SQL query to show the track id, track name, song length, price, price per millisecond, and price per second.

13. Challenge: You are interested in pricing how much it would cost to store EVERY track in your collection on Google Cloud Storage. Given the pricing statement on the [Google Storage Pricing Page](https://cloud.google.com/storage/pricing) under the heading "General pricing, Multi-Regional Storage (per GB per Month)," 

* Write a SQL query to calculate the size of the storage needed, in Gibibytes. Gibibytes are described on that same [Google page](https://cloud.google.com/storage/pricing) as follows: "Project storage usage and bandwidth usage are calculated in gigabytes (GB), where 1GB is 2<sup>30</sup> bytes. This unit of measurement is also known as a gibibyte (GiB). Similarly, 1TB is 2<sup>40</sup> bytes, i.e. 1024 GBs." 
* Your query should also produce the monthly price of the storage needed. For example, if you calculate that you have 5 GB of data, and each GB costs $10 to store, the total monthly storage price will be $50.

## What to turn in
Turn in a file or paste your answers into the 'Day4' lab on Moodle. Turn in as many questions as you can, and work on the others outside of class for practice!
