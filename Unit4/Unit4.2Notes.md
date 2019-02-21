## 4.2 INNER JOIN
An `INNER JOIN` statement collects the rows that match the criteria from two or more tables with at least one column in common. In the Venn diagrams above, the `INNER JOIN` is the one in the middle of the diagram. (All the other `JOIN`s shown in the diagram are variations of an `OUTER JOIN`. We will cover `OUTER JOIN` in section 4.3.)

Another way to recognize an `INNER JOIN` is to locate the following very common pattern: Look for one table to act as a "lookup table", sometimes called a "parent" table, and there is another "child" table that uses some sort of code or abbreviation to refer back to the primary key of the parent table. 

### 4.2.1 INNER JOIN Example: Simple lookup table
In the *World* database, suppose we want to find out which Country each City is in. We want to list each *City* and its Country *Name*. However, the *City* table only lists the country's *Code* but not the country's *Name*. 

In this example, *City* is the child table and *Countries* is the parent table, or lookup table. Notice how the *Code* shown in the *City* table matches up to the PK (*CountryCode*) column of the parent table. This is what we mean when we might say, "The child table refers back to the parent table."

Without knowing how to do a `JOIN` between the two tables, the best we can do is:

```sql
SELECT CityName as City, CountryCode
FROM City;
```
Which yields the following:

![image of cities and country codes](https://github.com/megansquire/CSC301Spr2019/blob/master/images/4.2.png)

But what does AFG mean? What is NLD? Without joins, we have to manually look up each *CountryCode* in the parent (Countries) table to see what it means. That's awkward.

In the diagram (or ERD, for "entity relationship diagram") below, I have circled the columns in common between the three tables - these are now shown in red. These columns all contain the same type of data, the *CountryCode*. 

![ERD for the world database](https://github.com/megansquire/CSC301Spr2019/blob/master/images/4.3.png)

Since we have columns in common between tables, we can `JOIN` on one or more of them in order to get the information we need in a single query:

```sql
SELECT City.CityName as 'City Name', Country.CountryName as 'Country Name'
FROM City
INNER JOIN Country
ON City.CountryCode = Country.Code;
```
Another way to write this query using table aliases:
```sql
SELECT c.CityName as 'City Name', co.CountryName as 'Country Name'
FROM City c
INNER JOIN Country co
ON c.CountryCode = co.Code;
```
You can also flip the order of the tables:
```sql
SELECT City.CityName as 'City Name', Country.CountryName as 'Country Name'
FROM Country co
INNER JOIN City c
ON co.Code = c.CountryCode;
```
![results from join command](https://github.com/megansquire/CSC301Spr2019/blob/master/images/4.4.png)

In that example, the first column (labeled "City") comes from the *City* table, and the second column, labeled "Country", comes from the *Country* table. We used the "columns in common" *Code* and *CountryCode* to construct the `JOIN`, but we don't have to show that column in common if we don't want to. (And in this case, we chose not to show it.)

> Note: In the ERD, there is a "key" icon next to this column in the two parent tables. The "columns in common" all have the same data type also.

### 4.2.2 INNER JOIN Example 2: Adding an aggregate function
In the *Hotels* database, suppose we want to show each hotel name, as well as a count of how many rooms each hotel has. To construct this query, we know we will need the *hotel* table (to get the name of the hotels) and we will need the *hotel_room* table to count the number of rooms. These two tables have one column in common (the column *hno*), so that is the column we will `JOIN` them together on.

Sometimes an ERD will show lines between the tables, indicating which columns are in common. In the ERD below, the common columns are also shown colored.

![ERD for the hotel database](https://github.com/megansquire/CSC301Spr2019/blob/master/images/4.5.png)

```sql
SELECT h.hname, count(hr.hno)
FROM hotel h
INNER JOIN hotel_room hr
        ON h.hno = hr.hno
GROUP BY 1
ORDER BY 2 DESC;
```
### 4.2.3 INNER JOIN Example 3: Selecting from three tables
Does any customer have more than one reservation at any of our hotels? Show the customer's last name, the name of the hotel, and count how many reservations they have. 

For this query, we need three tables: *hotels* (to get the hotel name), *hotel_reservation* (to count the number of reservations), and *hotel_customer* (to get the customer's last name).

```sql
SELECT hotel.hno, hotel.hname, hotel_customer.lname, count(hotel_reservation.rno) 
FROM hotel 
INNER JOIN hotel_reservation 
  ON hotel.hno = hotel_reservation.hno 
INNER JOIN hotel_customer 
  ON hotel_reservation.cno = hotel_customer.cno 
GROUP BY 1,2,3 
ORDER BY 4 DESC;
```
Yes, the customer ToolWare has two reservations at the same hotel (if you look them up, they are on different days).

We can also re-write this query using table aliases instead of the full table names:

```sql
SELECT h.hno, h.hname, hc.lname, count(hr.rno) 
FROM hotel h
INNER JOIN hotel_reservation hr
  ON h.hno = hr.hno 
INNER JOIN hotel_customer hc
  ON hr.cno = hc.cno 
GROUP BY 1,2,3 
ORDER BY 4 DESC;
```
### 4.2.4 Common INNER JOIN Errors

1. JOINing on the wrong column. Just because two tables both have a column called *id* doesn't mean that's the column in common! Remember the column in common has to represent the **exact same data** in each table.
2. Forgetting the `ON` statement, and just selecting from both tables. This will result in a "cartesian product" or `CROSS JOIN` between both the tables (all the rows in one table multiplied by all the rows in the second table). Sometimes we do want a CROSS JOIN (see section 4.4.4) but not always.
3. If you have more than two tables in the `JOIN`, doing too few `JOIN` conditions will produce a semantic error. You must have at least n-1 `JOIN` conditions, where n is the number of tables in the statement. For example, if you have 3 tables that you need to connect together, you need to have 2 `JOIN` conditions.

### 4.2.5 Foreign Keys

Think of an example where in the child table, there is a column that points back to a value in the parent table. (Perhaps the  `CountryCode` column in `City` points back to the `Code` column in `Countries`?) This column in the child table is called the "foreign key". 

Foreign keys enforce a simple rule: the data that you put into the child table *must* be already found in the parent table in order to be entered into the child table. 

In other words, you can't enter a value of "XFT" as the `CountryCode` in `City` table unless a country with that value ("XFT") has *already* been entered in the `Countries` table.

### 4.2.6 Locating your ERD
Sometimes you can get an ERD from the Designer view of PhpMyAdmin:

![designer in phpmyadmin](https://github.com/megansquire/CSC301Spr2019/blob/master/images/4.6.png)

