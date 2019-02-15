## 4.5 Subqueries
Subqueries are a way to let us embed the result of one query as the column or criterion for another query.

### 4.5.1 Correlated vs Non-Correlated subqueries

There are 2 main types of subqueries: correlated and non-correlated.

#### 4.5.1.1 Non-correlated subqueries
Non-correlated subqueries can be pulled out of the query and run by themselves. These are the easier of the two types of subqueries, both to think about and for the database to process.

With non-correlated subqueries, the entire subquery is run first, and then the outside query is run based on the results returned from the subquery. 

##### Non-correlated Example 1
```sql
SELECT City.CityName, Country.CountryName, City.Population
FROM City
INNER JOIN Country  ON City.CountryCode = Country.Code
WHERE City.Population = (SELECT max(Population) FROM City);
```
This *might* give results equivalent to the following. We say *might* because we have to assume there were not two cities with the exact same population (a "tie"):
```sql
SELECT City.CityName, Country.CountryName, City.Population
FROM City
INNER JOIN Country  ON City.CountryCode = Country.Code
ORDER BY 3 DESC
LIMIT 1;
```
> We need to be careful of ties. What if there were two values that had that same max population?

##### Non-correlated Example 2
"Tell me about the Cities with SurfaceArea that are greater than the surface area of the largest English-speaking City"
```sql
SELECT City.CityName, Country.CountryName, City.SurfaceArea
FROM City
INNER JOIN Country ON City.CountryCode = Country.Code
WHERE City.SurfaceArea > 
 (SELECT max(City.SurfaceArea) 
  FROM City 
  INNER JOIN Country ON City.CountryCode = Country.Code 
  INNER JOIN CountryLanguage ON Country.Code = CountryLanguage.CountryCode   
  WHERE CountryLanguage.Language = 'English');
```
##### Non-correlated Example 3
"Count all the languages for each country, and give me the country with the most languages"
```sql
SELECT MAX(innerTable.num) AS num
  FROM 
    (
      SELECT countrycode, COUNT(*) AS num 
      FROM CountryLanguage 
      WHERE isofficial='T' 
      GROUP BY countrycode -- don't end subquery with a ;
    ) AS innerTable
```
Couldn't this be done with a count, ORDER BY, and LIMIT?

#### 4.5.1.2 Correlated subqueries
Correlated subqueries are a little harder. These are when the columns inside the subquery are also in the outside query.

##### Correlated Example:
```sql
SELECT c.cust_id
FROM customer c
WHERE 10 < (SELECT count(*) FROM account a WHERE a.cust_id = c.cust_id);
```
##### Correlated example (this one is from [wikipedia](https://en.wikipedia.org/wiki/Correlated_subquery)):
```sql
 SELECT employee_number, name
   FROM employees AS emp
   WHERE salary > (
     SELECT AVG(salary)
       FROM employees
       WHERE department = emp.department);
```

##### Final example

Here, I took that same Wikipedia example and re-wrote it using our own `employees` database and added some stuff to make it more interesting.

This query shows every employee, their department number, the avg salary in the department, and the highest salary of these employees. Only employees are shown who have a high salary that is less than the department average.

```sql
SELECT emp.emp_no, 
       emp.last_name, 
       de.dept_no, 
       (SELECT avg(salary) 
           FROM salaries 
           INNER JOIN dept_emp 
             ON salaries.emp_no = dept_emp.emp_no 
           WHERE dept_emp.emp_no = emp.emp_no) as 'avg dept sal', 
       max(sal.salary) as 'emp highest sal'
FROM employees AS emp 
INNER JOIN salaries as sal 
  ON emp.emp_no = sal.emp_no 
INNER JOIN dept_emp AS de 
  ON de.emp_no = emp.emp_no
WHERE sal.salary < ( SELECT AVG(salaries.salary) 
                     FROM salaries 
                     INNER JOIN dept_emp de 
                     ON salaries.emp_no = de.emp_no 
                     WHERE de.emp_no = emp.emp_no)
GROUP BY 1,2,3,4  
```
What makes this a correlated subquery is that the inner queries use a column `emp.emp_no` that was created in the outer query.

Here are the first few rows of the result:

![salary](https://github.com/megansquire/CSC301Fall2018/blob/master/images/4.7.png)

### 4.5.2 Things to know about subqueries:

Most of the subqueries you will see in this class will be of the *non-correlated* type. They will be generally used to look up something where one query acts as a "temp" table for another ("outside") query.

Many subqueries (especially correlated ones) are generally inefficient and can be re-written to use a JOIN instead. Subqueries are usually quite expensive for the database to process. Use sparingly!

Another important note about subqueries is that they must return only one type of item. Notice in the examples shown, the subquery part always only returns one thing: either a max, a count, or a single column in the case of an IN query.

Sometimes PHPMyAdmin acts weird when you try to export the results of a subquery.
