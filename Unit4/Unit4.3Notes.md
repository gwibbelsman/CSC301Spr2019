## 4.3 OUTER JOIN
The `OUTER JOIN` statement is used when we want to connect tables, and we want to show records from one or more tables *even if* there is no match. 

How is an `OUTER JOIN` different than an `INNER JOIN`? First, we'll recap `INNER JOIN`:
* Recall that the `INNER JOIN` is based on equality between the values in two or more tables in one or more "columns in common" between the tables
* In the `INNER JOINs` we've seen so far, we use an equals(=) sign to indicate the column in common. `INNER JOIN` in this format are sometimes also called an *equi-join*. 
* We use an `INNER JOIN` when we want to show only the rows that match a value in *both* tables. If there is not a matching value in common in both tables, the row will not be shown. 
* `INNER JOIN`s are by far the most common type of `JOIN`.

In the case of the `OUTER JOIN`, we are doing the opposite: we want to show rows even if there is no equal value in both tables. 

`OUTER JOIN`s, therefore, are used in the following case, only:
* we want to select values from multiple tables, and
* we want to show all the rows, regardless of whether they have a match in the other table.

> Sometimes, as we saw in the [Venn diagram shown in Section 4.1](https://github.com/megansquire/CSC301Spr2019/blob/master/Unit4/Unit4.1Notes.md), you will see `LEFT OUTER JOIN` abbreviated as `LEFT JOIN`. I don't usually do this because I like to be very clear that I am doing an outer join, but you can use it if you like. `RIGHT OUTER JOIN` is synonymous with `RIGHT JOIN` and `LEFT OUTER JOIN` is synonymous with `LEFT JOIN`.

### 4.3.1 OUTER JOIN Example 1: simple
Suppose we have a list of *customers*, and a list of *reservations*, and we want to list all customers and reservations, but we also want to list *customers* who don't have a *reservation* at this time.

To do this, we will need to join all the *hotel* customers, and count the reservations from *hotel_reservations*. I will put the *hotel_customer* table on the left (first in the query), so that I can do a `LEFT OUTER JOIN`.

```sql
SELECT hc.cno, hc.lname, hr.rno 
FROM hotel_customer hc 
LEFT OUTER JOIN hotel_reservation hr 
  ON hc.cno = hr.cno;
```
I did choose to use table aliases in this query (**hc** for *hotel_customer* and **hr** for *hotel_reservation*).

### 4.3.2 OUTER JOIN Example 2: adding an aggregate
Suppose we have a table of *hotels* and a table of *hotel_reservations*, and we want to count reservations for all hotels, even if a particular hotel has no reservations:

```sql
SELECT hotel.hno, hotel.hname, count(hotel_reservation.rno)
FROM hotel 
LEFT OUTER JOIN hotel_reservation 
  ON hotel.hno = hotel_reservation.hno 
GROUP BY 1,2
ORDER BY 3 DESC;
```
Note that we did NOT use table aliases in that query. (No real reason, just wanted to show the query without them.) Here is the same query using the table aliases:
```sql
SELECT h.hno, h.hname, count(hr.rno)
FROM hotel h
LEFT OUTER JOIN hotel_reservation hr
  ON h.hno = hr.hno 
GROUP BY 1,2
ORDER BY 3 DESC;
```
We can also re-write a `LEFT OUTER JOIN` as a `RIGHT OUTER JOIN` by switching the order of the tables on the `FROM` line:

```sql
SELECT h.hno, h.hname, count(hr.rno)
FROM hotel _reservation hr
RIGHT OUTER JOIN hotel h
  ON h.hno = hr.hno 
GROUP BY 1,2
ORDER BY 3 DESC;
```
One other thing to know about `OUTER JOIN`s: You can mix-and-match `JOIN`s, although it is uncommon to do so, so be sure this is really what you want before you construct a complicated query. You can have a long statement where you `INNER JOIN` some tables and `OUTER JOIN` others.

## 4.3.3 FULL OUTER JOIN

There is no full join syntax for MySQL. Use this format instead:

```sql
SELECT * FROM tableA
LEFT JOIN tableB ON tableA.id = tableB.id
UNION
SELECT * FROM tableA
RIGHT JOIN tableB ON tableA.id = tableB.id
```
