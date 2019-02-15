## 4.4 More facts about JOINS
These are the types of things you might also see on a quiz or interview question.
### 4.4.1 Equi-join
The standard `INNER JOIN` where we use equality ("=") to find the intersection for the columns in common is also called an "equi-join".

Question to ponder: Is it possible to use a different Boolean operator besides the equals sign('=')? Like this: 
```sql
...
tableA INNER JOIN table ON tableA.id > tableB.id;
```
or does that need to be a `WHERE` clause? How can we test this?

### 4.4.2 Natural JOIN
There is a format of equi-join called `NATURAL JOIN` that looks like this:

```sql
SELECT * 
FROM tableA 
NATURAL JOIN tableB;
```
#### Rules for Natural Joins:
* There must be some identically-named column in common between the two tables, and this identically-named column must be the same data type, same length, and have the same logical purpose in both tables;
* You will return all columns from tableA as well as all columns from tableB;
* You will return all rows that have a match in the identically-named column, in both tableA and tableB.

#### Example: Show all the hotel names, hotel ids, and room types.
```sql
SELECT hr.hno, h.hname, hr.roomtype
FROM hotel h 
NATURAL JOIN hotel_reservation hr;
```
#### Example: Show everything about hotels and reservations
```sql
SELECT *
FROM hotel h 
NATURAL JOIN hotel_reservation hr;
```
### 4.4.3 THETA vs ANSI style
There is an older style of `INNER JOIN` syntax that doesn't use those `INNER JOIN...ON` keywords. Sometimes you will still see it in use. It looks like this:
```sql
SELECT tableA.foo, tableB.bar
FROM tableA, tableB
WHERE tableA.widgetID = tableB.widgetID;
```
This older style is sometimes called *theta-style* join, and the newer `INNER JOIN...ON` style is called an *ANSI* join.

Here is a theta-style JOIN example using the hotel schema:

```sql
SELECT h.hname, count(hr.hno)
FROM hotel h, hotel_room hr
WHERE h.hno = hr.hno
GROUP BY 1
ORDER BY 2 DESC;
```

### 4.4.4 CROSS JOIN
When we were first learning `JOIN` syntax, I mentioned that a common error is leaving off the `JOIN` condition when you don't mean to. Turns out, there is actually a term for this, and sometimes you might want to do it on purpose. It is called a `CROSS JOIN`. 
```sql
SELECT tableA.foo, tableB.bar
FROM tableA, tableB;
```
Another way to write a CROSS JOIN:
```sql
SELECT tableA.foo, tableB.bar
FROM tableA
CROSS JOIN tableB;
```
This will return all the rows in A crossed against all the rows in B. Try it in the real database with two tables that are small.

You will see that a CROSS JOIN will return A \* B rows. If table A has 10 rows and table B has 30 rows, a `CROSS JOIN` will get you 300 rows. Try it on the *recipes* database with two small tables, for example: 
```sql
SELECT * FROM recipes, recipe_classes;
```

Is the same as:

```sql
SELECT * FROM recipes 
CROSS JOIN recipe_classes
```

`CROSS JOIN` is sometimes called a Cartesian Product. Here is a [Stack Overflow Q&A](http://stackoverflow.com/questions/11861417/what-is-the-difference-between-cartesian-product-and-cross-join) about this.
