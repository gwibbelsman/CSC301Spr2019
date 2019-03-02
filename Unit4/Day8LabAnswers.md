# Day 8 Lab Answers: Joins and Subqueries
# Goal
Practice writing subqueries and joins.

## Questions
1. Using the *world* database, write a query to display the Continent, Country Name, and Surface Area for the country on each continent that has the highest surface area. [Hint](https://stackoverflow.com/a/1813766)

Sample answer:

![sample answer for q2](https://github.com/megansquire/CSC301Fall2018/blob/master/images/day8lab.2.png)

```sql
SELECT c1.Continent, c1.Name, c1.SurfaceArea
FROM Country c1
LEFT OUTER JOIN Country c2
  ON (c1.continent = c2.continent AND c1.SurfaceArea < c2.SurfaceArea)
WHERE c2.continent IS NULL
AND c1.SurfaceArea  > 0
ORDER BY 1 ASC;
```

Is it possible to do this same query without an OUTER JOIN? Some folks tried this:

```sql
SELECT c1.Continent, c1.Name, c1.SurfaceArea 
FROM Country c1 
WHERE c1.SurfaceArea IN (select max(SurfaceArea) from Country group by Continent)
```

The problem with this approach is that the subquery returns the following:

![day8 subquery attempt](https://github.com/megansquire/CSC301Fall2018/blob/master/images/day8lab.4.png)

Since there is more than one row here, we adjusted the WHERE clause to use an IN. Now any country with a Surface Area that happens to match that set will be returned. So, any country on any continent with a surfaceArea that happens to match one of these values will be returned! (With the very specific SurfaceArea numbers, this is not likely to happen, but it could. Clearly this approach is not great.) 

2. Using the *employees* database, write a query to display the employee number, first name, last name, and maximum salary for everyone with the last name 'Facello,' but only include those who make more money than the person named 'Georgi Facello'. Do not assume you know Georgi's employee number in your final query. (Look him up by name.)

Sample answer

![sample answer for q3](https://github.com/megansquire/CSC301Fall2018/blob/master/images/day8lab.3.png)


```sql
SELECT e1.emp_no, e1.first_name, e1.last_name, max(s1.salary)
FROM employees e1
inner join salaries s1
on e1.emp_no = s1.emp_no
WHERE s1.salary > 
(SELECT max(s2.salary) FROM salaries s2
 inner join employees e2
 on e2.emp_no = s2.emp_no 
 WHERE e2.first_name = 'Georgi' and e2.last_name = 'Facello')
AND e1.last_name = 'Facello'
GROUP BY 1,2,3
order by e1.first_name ASC;
```

3. Using the *wine* database, list all the countries in the wine database, and the count of customers that have that country listed. If there are no customers from that country, you don't need to list it. Hint: perform a "sanity check" on this result and make sure it is accurate! :) 
```sql
SELECT wc.country_id, wc.country, count(c.cust_id)
FROM wine_countries wc
INNER JOIN wine_customer c
  ON wc.country_id = c.country_id 
GROUP BY 1,2;
```
We could also use a NATURAL JOIN here:
```sql
SELECT wc.country_id, wc.country, count(c.cust_id)
FROM wine_countries wc
NATURAL JOIN wine_customer c
GROUP BY 1,2;
```

4. Using the *wine* database, list all countries (id and name), and their customer counts, but be sure to list the country even if their customer count is 0.
```sql
SELECT wc.country_id, wc.country, count(c.cust_id)
FROM wine_countries wc
LEFT OUTER JOIN wine_customer c
  ON wc.country_id = c.country_id 
GROUP BY 1,2;
```

5. Using the *wine* database, write a query with a subquery to display the wine_id, wine_name, year, and cost for the most expensive wine(s) in the inventory. DO NOT USE A LIMIT.

Sample answer:

![sample answer for q1](https://github.com/megansquire/CSC301Fall2018/blob/master/images/day8lab.1.png)

Solution strategy: find the max cost for any wine (29.92) in a subquery, pass that to the outer query and select out only the wines that have that matching cost. 

```sql
SELECT w.wine_id, w.wine_name, w.year, wi.cost
FROM wine w
INNER JOIN wine_inventory wi
ON w.wine_id = wi.wine_id
WHERE wi.cost = (SELECT max(wi.cost) FROM wine_inventory wi);
```
