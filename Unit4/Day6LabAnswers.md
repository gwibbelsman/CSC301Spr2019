# Day 6 lab answers

1. Write the SQL to print out every employee's first name, last name, gender, and job title. Put them in alphabetical order by last name. (Remember that it's ok that an employee may have had many job titles. Maybe she got promoted!)
```sql
SELECT e.last_name, e.first_name, e.gender, t.title 
FROM employees e 
INNER JOIN titles t 
  ON e.emp_no = t.emp_no
ORDER BY 1,2,4;
```

2. Write the SQL to print out every employee's first name, last name, gender, job title, and salary history. Put them in alphabetical order by last name, first name, title, then salary. NOTE: this query took about 17 seconds to run, so be patient.
```sql
SELECT e.last_name, e.first_name, e.gender, t.title, s.salary 
FROM employees e 
INNER JOIN titles t 
  ON e.emp_no = t.emp_no 
INNER JOIN salaries s 
  ON s.emp_no = e.emp_no 
ORDER BY 1,2,4,5;
```

3. Write the SQL to figure out what is the most common birth date for all employees. (Include year, month, and day, as well as the number of employees that have this birth date.)
```sql
SELECT birth_date, count(emp_no)
FROM employees
GROUP BY 1
ORDER BY 2 DESC 
LIMIT 1;
```

4. In the history of the company, how many managers has each department had? Put these in order from highest number of managers to lowest. Use the full department name, and show the department number, as well as the count.
```sql
SELECT d.dept_name, dm.dept_no, COUNT(dm.emp_no)
FROM dept_manager dm
INNER JOIN departments d
  ON dm.dept_no = d.dept_no
GROUP BY 1,2;
```

5. Write the SQL to find out what is the highest salary that each employee has ever received. List the employee's first and last name, and show these in the format "Last, First" (in alphabetical order by last name) and their highest salary.
```sql
SELECT MAX( salary ) , emp_no, CONCAT( last_name, ", ", first_name ) AS 'Name'
FROM salaries s
INNER JOIN employees e 
  ON s.emp_no = e.emp_no
GROUP BY 2,3
ORDER BY 3 DESC

```
6. Write the SQL to show each employee's information and the number of job titles they've had. But only show people who have had 3 or more job titles during their time at the company. Show the employee's first initial and last name (for example: M. Squire), and their employee id, and the count of jobs.

Here is a solution using ```substring()``` but you could also use ```left()```
```sql
SELECT CONCAT(SUBSTRING(e.first_name,1,1),". ", e.last_name), 
    e.emp_no,
    COUNT(t.title)
FROM titles t 
INNER JOIN employees e 
  ON t.emp_no = e.emp_no
GROUP BY 1,2
HAVING COUNT(t.title) >= 3;
```

7. Write the SQL to show each employee number, first and last names, and birth dates of employees who are some type of engineer, and the number of job titles they've had. Only show people who have had at least 2 engineer jobs and who were born in the 1950s. Put them in order by their birth date.
```sql
SELECT e.emp_no, e.first_name, e.last_name, e.birth_date, COUNT(t.title)
FROM employees e 
INNER JOIN titles t 
  ON e.emp_no = t.emp_no
WHERE t.title LIKE "%engineer%"
  AND YEAR(e.birth_date) BETWEEN 1950 AND 1959
GROUP BY 1,2,3,4
HAVING COUNT(t.title) >= 2
ORDER BY 4;
```
8. Write the SQL to show the information about employees who were employed in a given position for less than one day.
```sql
SELECT t.emp_no, e.first_name, e.last_name, t.from_date, t.to_date
FROM titles t
INNER JOIN employees e 
  ON t.emp_no = e.emp_no
WHERE DATEDIFF(t.to_date, t.from_date) < 1;
```

9. Write the SQL to show information about employees who are still employed. (We can use the to_date value that is '9999-01-01' to indicate that the employee is still employed, but this seems like a bit of a hack. Think about how the designers should have implemented the idea that an employee is still employed.) Show the employee's information (number, name, hire dates, quit dates), including current (highest) salary.
```sql
SELECT t.emp_no, e.first_name, e.last_name, t.from_date, t.to_date, MAX(s.salary)
FROM titles t
INNER JOIN employees e 
  ON t.emp_no = e.emp_no
INNER JOIN salaries s 
  ON s.emp_no = e.emp_no
WHERE YEAR(t.to_date) = '9999'
AND YEAR(s.to_date) = '9999'
GROUP BY 1,2,3,4,5;
```
