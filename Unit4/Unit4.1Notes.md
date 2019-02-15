# Unit 4: Joins
## 4.1 What are joins for?
So far we have only executed SQL statements on a single table at a time. However, many of the SQL commands - including `SELECT` - can use data from more than one table at a time. 

A SQL `JOIN` statement will allow us to connect these tables, using these common columns. The purpose of joining two or more tables together is to connect them so we can make more complex, interesting queries.

Below you will see the most common `JOIN` cheat sheet, and many students have reported seeing it in various cubicles during interviews, internships, or after they graduate.

![SQL Join Venn Diagram](https://github.com/megansquire/CSC301Spr2019/blob/master/images/4.1.jpg?raw=true)

### 4.1.1 Quick summary: How to Solve JOINs
**Step 1**: Looking at the entity relationship diagram (ERD) for your database, identify the columns you need in the final output. (This will become your `SELECT` line.)

**Step 2**: Looking at the ERD, identify which tables those columns are found in. (This will become the list of tables in the `FROM` line, and in the `INNER JOIN` or `OUTER JOIN` lines.)

**Step 3**: For all the tables in Step 2, use the ERD to find the columns in common between them. (These will become the `ON` portion of the `INNER JOIN...ON ...` lines)

**Step 4**: Put the tables in order based on which ones are attached to each other, or which ones have column(s) in common. Trace a path through the tables. (This will tell you what order to put the `INNER JOIN ... ON...` lines in)

**Step 5**: For each "column in common" match, identify whether you need to show ALL the items from one table and only the matching items in the other table. If so, you will need an `OUTER JOIN`. Use the Venn diagram chart to help.

**Step 6**: Ad bells and whistles. Do you need a `WHERE` clause? Do you need a `LIMIT`? `ORDER BY`? Do you have an aggregate column that requires grouping? Do you need a `HAVING` in order to reduce the number of groups shown? If so, add aggregate functions and the associated `GROUP BY` (and `HAVING` if necessary). Do you need any other functions on the `SELECT` line? 
