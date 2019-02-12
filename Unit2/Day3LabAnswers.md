# Day 3 lab Answers

1. Write a SQL query to find the percentage of Alamance County (NC) citizens who are living in poverty. Show the area name and percent living in poverty.
```sql
SELECT area_name, pov_pct
FROM poverty2012 
WHERE area_name='Alamance County';
```
2. Write a SQL query to find the percent of NC residents who are living in poverty.

This solution asks for the main state-level figure:
```sql
SELECT area_name, pov_pct 
FROM `poverty2012` 
WHERE area_name = 'North Carolina'

18.0
```
You could also attempt this one with a average of the sub-figures, however note that you will probably not get the same value as the above query. Why?
```sql
SELECT state, avg(pov_pct) 
FROM poverty2012
WHERE state = 'NC'
GROUP BY state;

20.08713
```
Perhaps we need to exclude the state average (18.0%) itself in our average:
```sql
SELECT state, avg(pov_pct) 
FROM poverty2012 
WHERE state = 'NC' 
AND area_name != 'North Carolina'
GROUP BY state;

20.10800 
```
Here, we still get a number higher than 18, which is the statewide figure provided. I guess we just don't know why they are different in this data set. A mystery. Perhaps there are unincorporated cities that did not report data into the county figures.

3. Write a SQL query to list the county names and poverty rates for NC counties whose rate is higher than the NC rate. Put them in order from highest down to lowest. (You may 'hardcode' in the NC rate. In future classes we will learn how to look this up automatically, but we haven't learned how to do that yet.)
```sql
SELECT area_name, pov_pct
FROM poverty2012 
WHERE state = 'NC' 
  AND pov_pct > 18 -- no quotes needed here since 18 is a number
ORDER BY 2 DESC;
```
PS, here is how we would do it without "hardcoding" the number 18. This solution requires something called a subquery (we'll get to these next week):
```sql
SELECT area_name, pov_pct
FROM poverty2012 
WHERE state = 'NC' AND pov_pct > 
    (SELECT pov_pct 
    FROM poverty2012 
    WHERE area_name='North Carolina')
ORDER BY 2 DESC;
```
4. Write a SQL query to list the top 10 counties (also list the state and poverty percentage) in the United States with the highest poverty rates. Just in case there are ties, sort them numerically and then alphabetically to break the tie. *Does this query require an aggregate?*
```sql
SELECT state, area_name, pov_pct
FROM poverty2012 
ORDER BY 3 DESC
LIMIT 10;
```

5. Write a query to find the City name and population for the city that has the highest population. Hint: you might need a LIMIT here.
```sql
SELECT Name, MAX(population) 
FROM City
GROUP BY 1 
ORDER BY Population DESC 
LIMIT 1;
```

6. List every head of state from the countries table and how many countries they are in charge of. List them in order of most to least countries.
```sql
SELECT HeadOfState, COUNT(Name) AS CountriesRuled 
FROM  Country 
GROUP BY HeadOfState
ORDER BY 2 DESC;
```

7. Write the SQL to list each HeadOfState, add up how many countries that person is in charge of, sort them from most to least, but only show the HeadsOfState that are in charge of more than 1 country.
```sql
SELECT HeadOfState, COUNT(Name) AS CountriesRuled 
FROM  Country 
GROUP BY 1 
HAVING CountriesRuled > 1 -- HAVING is required here since we want to filter out the results AFTER counting them
ORDER BY 2 DESC;
```

8. Write the SQL to list each HeadOfState and add up how many people that person is in charge of, sort them from most people to least, but ONLY include the HeadsOfState that are in charge of North American countries.
```sql
SELECT HeadOfState, SUM(Population) AS Pop 
FROM  Country
WHERE Continent = "North America" 
GROUP BY HeadOfState 
ORDER BY 2 DESC;
```

9. Write the SQL to count major cities by country code, but only list the countries that begin with the letter A and have 2 or fewer major cities.
```sql
SELECT countrycode, COUNT(*) 
FROM City 
WHERE countrycode LIKE 'A%' 
GROUP BY 1 
HAVING count(*) <=2;
```
