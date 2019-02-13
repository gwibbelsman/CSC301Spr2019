# Extra Practice Questions for Unit 2

## Questions
Using the World database, write the following queries and save them to a .txt file; upload that file to Moodle.
1. Write a query to find the highest population in the Countries table. Only show the population number in your result.
1. Write a query to find the City name and population for the city that has the highest population.
1. List every head of state from the countries table and how many countries they are in charge of. List them in order of most to least countries.
1. Write the SQL to list each HeadOfState, add up how many countries that person is in charge of, sort them from most to least, but only show the HeadsOfState that are in charge of more than 5 countries.
1. Write the SQL to list each HeadOfState and add up how many people (population) that person is in charge of, sort them from most people to least.
1. Write the SQL to list each HeadOfState and add up how many people that person is in charge of, sort them from most people to least.
1. Write the SQL to count cities by country code, but only list the countries whose code begins with the letter T and have 3 or more major cities.
1. Write the SQL to calculate average life expectancy by continent.
1. What is the average lifespan for countries with either a government form that has "Republic" somewhere in its form of government, or that has "Monarchy" somewhere in its form of government. Your result will list various Republics and a number (average), and Monarchies and a number (average). 

Example of what the answer might look like:

| GovernmentForm | Average life expectancy |
|--------------- | ----------------------- |
| Constitutional Monarchy	| 71.86897 |
| Constitutional Monarchy (Emirate)	| 76.10000 |
| Constitutional Monarchy, Federation	| 76.95000 |
| Federal Republic	| 68.43333 |
| Islamic Republic	| 63.15000 |
| Monarchy	| 60.18000 |
| Monarchy (Emirate) | 73.00000 |
| Monarchy (Sultanate) | 72.70000 |
| Parlementary Monarchy | 69.20000 |
| People's Republic	| 71.40000 |
| Republic | 62.45902 |
| Socialistic Republic | 72.06667 |

## Answers
1. Write a query to find the highest population in the database. ONly show the population number in your result.
```sql
SELECT MAX(population) 
FROM City;
```
2. Write a query to find the City name and population for the city that has the highest population. Hint: you might need a LIMIT here.
```sql 
SELECT Name, MAX(population) 
FROM City
GROUP BY 1 
ORDER BY 2 DESC 
LIMIT 1;
```
3. List every head of state from the countries table and how many countries they are in charge of. List them in order of most to least countries.
```sql
SELECT HeadOfState, COUNT(Name) AS CountriesRuled 
FROM  Country 
GROUP BY HeadOfState
ORDER BY 2 DESC;
```
4. Write the SQL to list each HeadOfState, add up how many countries that person is in charge of, sort them from most to least, but only show the HeadsOfState that are in charge of more than 5 countries.
```sql
SELECT HeadOfState, COUNT(Name) AS CountriesRuled 
FROM  Country 
GROUP BY 1 
HAVING CountriesRuled > 5 
ORDER BY 2 DESC;
```
5. Write the SQL to list each HeadOfState and add up how many people (population) that person is in charge of, sort them from most people to least.
```sql
SELECT HeadOfState, SUM(Population) AS Pop 
FROM  Country
GROUP BY 1 
ORDER BY 2 DESC;
```
6. Write the SQL to list each HeadOfState and add up how many people that person is in charge of, sort them from most people to least.
```sql
SELECT HeadOfState, SUM(Population) AS Pop 
FROM  Country
GROUP BY HeadOfState 
ORDER BY 2 DESC;
```
7. Write the SQL to count major cities by country code, but only list the countries that have a code beginning with the letter T and have 3 or more major cities.
```sql
SELECT countrycode, COUNT(*) 
FROM City 
WHERE countrycode LIKE 'T%' 
GROUP BY 1 
HAVING count(*) >= 3;
```
8. Write the SQL to calculate average life expectancy by continent.
```sql
SELECT Continent, AVG(LifeExpectancy) 
FROM Country 
GROUP BY 1;
```
9. What is the average lifespan for countries with either a government form that has "Republic" somewhere in its form of government, versus those that have "Monarchy" somewhere in its form of government. Your result will list various Republics and a number (average), and Monarchies and a number (average). NOTE: ideally, we'd like to combine the monarchies all together and the republics all together. That is harder. Let's keep this in mind for the future.
```sql
SELECT GovernmentForm, AVG(LifeExpectancy) 
FROM  Country
WHERE GovernmentForm LIKE  "%Republic%"
  OR GovernmentForm LIKE  "%Monarchy%" 
GROUP BY 1;
```
