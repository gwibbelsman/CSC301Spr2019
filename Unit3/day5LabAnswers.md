# Day 5 Lab Answers
## Question 4, attempt 1 - a bit of a hack
After noticing that there were only two months of data in the table, I used two queries, one for May and one for June:
```sql
INSERT INTO sentiment140_dates (id, date_of_tweet, user, tweet_text)
SELECT id, 
concat(right(date_of_tweet,4),
  '-05-',
  substring(date_of_tweet,9,2),
  ' ',
  substring(date_of_tweet,12,8)), 
user, 
tweet_text 
FROM `sentiment140_orig`
WHERE date_of_tweet like "%May%";

INSERT INTO sentiment140_dates (id, date_of_tweet, user, tweet_text)
SELECT id, 
concat(right(date_of_tweet,4),
  '-06-',
  substring(date_of_tweet,9,2),
  ' ',
  substring(date_of_tweet,12,8)), 
user, 
tweet_text 
FROM `sentiment140_orig`
WHERE date_of_tweet like "%Jun%";
```
## Question 4, attempt 2 - better!
Here is another - more sophisticated - way to approach the task (more on [str_to_date()](https://www.w3schools.com/sql/func_mysql_str_to_date.asp)):
```sql
INSERT INTO sentiment140_dates (id, date_of_tweet, user, tweet_text)
SELECT id, 
  STR_TO_DATE(REPLACE(date_of_tweet,'UTC',''), '%a %b %d %T %Y'), 
  user, 
  tweet_text 
FROM sentiment140_orig;
```

In this answer, we want to use the `str_to_date()` function to create a date item from any formatted string. The technique is to label all the parts of the string so that the function knows what to do with each piece - how to use that piece to make a date. First we throw out the 'UTC' part with a `replace()` function. Then we tell `str_to_date()` that `%a` stands for the weekday name, followed by `%b` for a Month abbreviation, `%d` for a day of the week, `%T` for a time, and finally a `%Y` for the year. Once you've labeled the parts of the string, MySQL can turn them into a date!

## Question 4, attempt 3 - even better!

Here we don't bother to remove "UTC", we just indicate where in the string to expect those three letters. 

```sql
INSERT INTO sentiment140_dates (id, date_of_tweet, user, tweet_text)
SELECT id, 
  STR_TO_DATE(date_of_tweet, '%a %b %d %T UTC %Y'), 
  user, 
  tweet_text 
FROM sentiment140_orig;
```

## Question 5
Here, we do the same thing for the dates, and we also add in a `char_length()` to count the number of characters in the tweet:
```sql
INSERT INTO sentiment140_chars (id, date_of_tweet, user, tweet_text, tweet_length)
SELECT id, 
  STR_TO_DATE(date_of_tweet, '%a %b %d %T UTC %Y'), 
  user, 
  tweet_text,
  CHAR_LENGTH(tweet_text)
FROM sentiment140_orig;
```
## Question 6 - CHALLENGE
`locate()` gets the character location of the first '/' anywhere after the 9th digit. This will be used as the third parameter to the `SUBSTRING()` function that finds the domain, then we subtract one to ignore that trailing '/'. Finally, we use `SUBSTRING` to extract just the domain part -- but we start with character 8 (ignore the first 7 characters: `http://`)
```sql
SELECT substring(substring(url, 1, locate('/',url,9)-1), 8) as 'Domain',
       count(*) as 'Count'
FROM sentiment140_urls
GROUP BY 1
ORDER BY 2 DESC;
```
