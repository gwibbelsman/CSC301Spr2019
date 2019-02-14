## World database
1. Write a SQL query to list each continent (Africa, North America, etc) in upper case, and show each region within that continent, and then count how many countries are in that region. Sort these in alphabetical order by continent and then by count. Hint: here is a screenshot of the results we want.
```sql
SELECT UPPER(Continent) as Continent, Region, COUNT(CountryName) as 'Count of Countries'
FROM Country
GROUP BY 1, 2 
ORDER BY 1, 3; 
```
2. Using the WORLD database tables, construct a SQL query to find countries that have a  country code that is the same as the first three letters of a country's name. For example, AFG = Afghanistan, and ALB = Albania. Hint: there are 76 results. 
```sql
SELECT Code, CountryName 
FROM Country
WHERE Code = left(upper(CountryName),3);
```
or, we can flip the order of upper() & left():
```sql
SELECT Code, CountryName 
FROM Country 
WHERE Code = upper(left(CountryName,3));
```
or, we can use a substring():
```sql
SELECT Code, CountryName
FROM Country
WHERE Code = substring(upper(CountryName),1,3);
```
3. Using the WORLD database tables, construct a SQL query that will list the countries from largest to smallest by land area. Print them so that the answer looks like this, in a single column. Your result will have 239 rows, one for each country.
```sql
SELECT concat(Code,"(",CountryName,"):",SurfaceArea," km squared" ) 
FROM Country 
ORDER BY SurfaceArea DESC;
```

## Employees database

4. Congratulations, you have been assigned to the birthday party planning committee for the company in the EMPLOYEE database. Write the SQL to print out a list showing each month of the year (numbered 1-12) and how many birthdays occur in that month. Put these in order by month.
```sql
SELECT month(birth_date), count(*) 
FROM employees
GROUP BY 1 
ORDER BY 1;
```
5. Assuming you can feed 100 people with one extra large birthday cake, how many cakes will you need each month? Round up so no one gets left out of the cake-fest like Milton in Office Space. Write SQL to show the month number, the number of birthdays that month, the number of cakes needed, and a calculation of the total cake budget (each cake costs $43.) Show this number with a dollar sign and commas for the thousands places (if needed), as follows:
```sql
SELECT month(birth_date), 
  count(*) as numBirthdays, 
    ceiling(count(*)/100) as numCakes, 
    concat('$',format(ceiling(((count(*)/100)*43)),2)) as cakeBudget 
FROM employees 
GROUP BY 1 
ORDER BY 1 asc;
```

## Music database
1. Which state **in the United States** have the most customers? 
```sql
SELECT state, COUNT(customerid) 
FROM Customer
WHERE country='USA'
GROUP BY state
ORDER BY 2 DESC
LIMIT 1;
```
2. Imagine that we would eventually like to draw a graph of the number of invoices by month and year. Write the SQL that will yield the data needed to make this graph. Put the data result set in order by year and then month. Display the name of the month, but put them in the order that they appear in time (January comes before February, then March, etc. )
```sql
SELECT YEAR(invoicedate), MONTH(invoicedate), MONTHNAME (invoicedate), COUNT(invoiceid) 
FROM Invoice
GROUP BY 1, 2, 3
ORDER BY 1, 2;
```
3. Imagine you are a customer service representative. You answer the phone and the person complaining on the other end says his name, and you hear him say something like "Louis" for this first name. However, you run a SQL command to search for first names like Louis and nothing comes up. Write the SQL command to find all the customer details for a selection of names that might sound like Louis. 

Hint, it should match names like Luis, Luís, Lewis and even Lucas, but without specifically naming any of those names in the query.

Another hint, check the list of MySQL [string functions](https://dev.mysql.com/doc/refman/5.7/en/string-functions.html)....
```sql
SELECT * 
FROM Customer
WHERE FirstName
SOUNDS LIKE "louis";
```
--OR--
```sql
SELECT * 
FROM Customer 
WHERE SOUNDEX('Louis') = SOUNDEX(FirstName);
```
4. On what day in history did your Music company make the most money? Write the SQL to calculate a total for each date. Format the total sales as currency. Display only the highest total date.
```sql
SELECT CONCAT(MONTH(invoiceDate),  
  "/", 
  DAY(invoicedate),  
  "/", 
  YEAR(invoiceDate)) AS 'Date', 
SUM(total) AS 'Total sales'
FROM Invoice
GROUP BY DATE(invoiceDate) 
ORDER BY 2 DESC
LIMIT 1;
```
--OR--
```sql
SELECT DATE_FORMAT(InvoiceDate,'%m/%d/%Y') AS 'Date', 
  SUM(Total) AS 'Total sales' 
FROM Invoice
GROUP BY 1 
ORDER By 2 DESC
LIMIT 1;
```
5. What day of the week do we make the most money? Write the SQL to show the days of the week (Sunday, Monday, etc) and the sum of all invoices presented on that day, ever. Sort the items in the order that the day appears in the week (so for example Sunday is first day, then Monday, etc).
```sql
SELECT DAYNAME(invoicedate), SUM(total) 
FROM Invoice
GROUP BY 1
ORDER BY DAYOFWEEK(invoicedate);
```
6. We want to find the Customers who have a Last Name that includes characters other than those found in the English alphabet. All these special characters will have a character length that is smaller than the actual length of the string in bytes. For example, the string Muñoz has only 5 characters, but the string has a length of 6, since the ñ character takes 2 bytes to store, rather than just one. Write the SQL to display the LastName, the length of the name in bytes, the length of the characters in the name in bytes, BUT only show the names where there is actually a difference between length and character length.
```sql
SELECT LastName, length(LastName), char_length(LastName) 
FROM Customer
WHERE length(LastName) != char_length(LastName);
```
7. Which song (track) is the most expensive per second? Write a SQL query to show the track id, track name, song length, price, price per millisecond, and price per second. 
```sql
SELECT trackid, name, milliseconds, unitprice, 
  (unitprice / milliseconds) AS "Price per millisecond", 
  (unitprice / milliseconds)*1000 AS "Price per second"
FROM Track
ORDER BY 6 DESC
LIMIT 1;
```
8. Challenge: You are interested in pricing how much it would cost to store EVERY track in your collection on Google Cloud Storage. Given the pricing statement on the [Google Storage Pricing Page](https://cloud.google.com/storage/pricing) under the heading "General pricing, Multi-Regional Storage (per GB per Month)," 
* Write a SQL query to calculate the size of the storage needed, in Gibibytes. Gibibytes are described on that same [Google page](https://cloud.google.com/storage/pricing) as follows: "Project storage usage and bandwidth usage are calculated in gigabytes (GB), where 1GB is 230 bytes. This unit of measurement is also known as a gibibyte (GiB). Similarly, 1TB is 240 bytes, i.e. 1024 GBs." 
* Your query should also produce the monthly price of the storage needed. For example, if you calculate that you have 5 GB of data, and each GB costs $10 to store, the total monthly storage price will be $50.
```sql
SELECT sum(bytes)/power(1024,3) as "Total size in Gbb",
round(sum(bytes)/power(1024,3)*.026,2) as "Monthly cost" 
FROM Track;
```
--OR--
```sql
SELECT sum(bytes)/power(2,30) as "Total size in Gbb", round(sum(bytes)/power(2,30)*.026,2) as "Monthly cost" 
FROM Track;
```
