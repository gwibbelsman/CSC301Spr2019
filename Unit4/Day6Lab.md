# Day 6 Lab
## Goal
Practice writing INNER JOINs using the `employees` database, and the ERD shown below.

![employees database erd](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day6lab.1.png)

## Questions
* NOTE: not every query requires an `INNER JOIN`. 
* NOTE 2: Be careful of over-matching the "columns in common". For example, the *to_date* and *from_date* columns appear in many tables, but because these aren't usually part of the PK (primary key, or "unique identifier") of any table, they probably aren't good candidates for "column in common". Better choices for columns in common will be *emp_no* for employees and *dept_no* for departments.

1. Write the SQL to print out every employee's first name, last name, gender, and job title. Put them in alphabetical order by last name, then first name, then job title. (Remember that it's ok that an employee may have had many job titles. Maybe she got promoted!) 
2. Write the SQL to print out every employee's first name, last name, gender, job title, and salary history (dollar figures are sufficient). Put them in alphabetical order by last name, first name, title, then salary. NOTE: this query took a few seconds to run, so be patient. 
3. Write the SQL to figure out what is the most common birth date (yyyy-mm-dd) for all employees. Which date has the highest number of employees?
4. In the history of the company, how many managers has each department had? Put these in order from highest number of managers to lowest. Use the full department name, and show the department number, as well as the count.
5. Write the SQL to find out what is the highest salary that each employee has ever received? List the employee's first and last name, and show these in the format "Last, First" (in alphabetical order by last name) and their highest salary.
6. Write the SQL to show each employee's information and the number of job titles they've had. But only show people who have had 3 or more job titles during their time at the company. Show the employee's first initial and last name (for example: M. Smith), and their employee id, and the count of jobs.
7. Write the SQL to show each employee number, first and last names, and birth dates of employees who are some type of engineer, and the number of job titles they've had. Only show people who have had at least 2 engineer jobs and who were born in the 1950s. Put them in order by their birth date.
8. Write the SQL to show the information about employees who were employed in a given position for less than one day.
9. Write the SQL to show information about employees who are still employed. (We can use the *to_date* value that is '9999-01-01' to indicate that the employee is still employed, but this seems like a bit of a hack. Think about how the designers *should* have implemented the idea that an employee is still employed.) Show the employees' current department and all their employment information, including current salary.

## What to turn in
Turn in a text file to Moodle with your answers.
