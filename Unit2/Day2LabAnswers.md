# Day 2 lab answers

1. Write the SQL to show what is the life expectancy for Afghanistan. Show the country name and the life expectancy.
```sql
SELECT CountryName, LifeExpectancy
FROM Country
WHERE CountryName = 'Afghanistan'; 
```
2. Write the SQL to show the country names and life expectancies for all countries with life expectancies below age 50.
```sql
SELECT CountryName, LifeExpectancy
FROM Country
WHERE LifeExpectancy < 50;
```
3. Show countries and the year that they became independent. Exclude any country with a 'null' value for independence.
```sql
SELECT CountryName, IndepYear
FROM Country
WHERE IndepYear IS NOT NULL;
```
4. What about the countries that never became independent (IndepYear is null). What is the deal? Show the country name, the fact that their independence year is null, the form of government and who the ruler is.
```sql
SELECT CountryName, IndepYear, GovernmentForm, HeadOfState
FROM Country
WHERE IndepYear IS NULL;
```
5. Sometimes it is tricky to deal with single quotes in data values. Special care must be taken to "escape" the quotation mark. Write a query to find any data values in the HeadOfState column of the country table that have a single quote in them. Write the query and give the name of the country (if any) in your answer.
```sql
SELECT CountryName, HeadOfState
FROM Country
WHERE HeadOfState LIKE "%'%"; -- here we use double quotes on the outside
```
or
```sql
SELECT CountryName, HeadOfState
FROM Country
WHERE HeadOfState LIKE '%\'%'; -- you can "escape" the single quote with a backslash since it is already enclosed in singles
```
or
```sql
SELECT CountryName, HeadOfState
FROM Country
WHERE HeadOfState LIKE '%''%'; -- you can "escape" the single quote with another single quote since it is already enclosed in singles
```
6. Write the SQL to show all known information about all cities. 
```sql
SELECT * 
FROM 'City';
```
7. Write the SQL to show the population and city name for the city called Kabul. 
```sql
SELECT CityName, Population 
FROM City 
WHERE CityName = 'Kabul';
```
8. Write the SQL to show the population and city name for both Kabul and Qandahar. 
```sql
SELECT CityName, Population 
FROM City 
WHERE CityName = 'Kabul' OR CityName = 'Qandahar';
```
or
```sql
SELECT CityName, Population
FROM City
WHERE CityName IN ('Kabul', 'Qandahar');
```
9. Write the SQL to show the population, country code, and city name for all cities in Afghanistan (use country code AFG). 
```sql
SELECT CityName, CountryCode, Population 
FROM City 
WHERE CountryCode = 'AFG';
```
10. Suppose we are interested in extreme minority official languages. These are official languages that are officially sanctioned by the government but have less than 10% of the population speaking them. Write a SQL query to show the language, the country, and the percentage. Only show official languages.
```sql
SELECT CountryCode, SpokenLanguage, Percentage 
FROM CountryLanguage 
WHERE IsOfficial = 'T' AND Percentage < 10;
```
11. CHALLENGE #1: How old is this data? How do you know this? Can you write a query to help prove this?
It's at least a few years old due to the fact that the US president in the data is listed as George W. Bush!
```sql
SELECT CountryName, HeadOfState
FROM Country
WHERE Code = "USA"; -- could also use country name here
```
