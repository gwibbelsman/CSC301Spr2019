# Day 5 lab
## Purpose
Practice with functions, INSERT, UPDATE using the `sentiment140_orig` table.
## What to do
1. Make a copy of the `sentiment140_orig` table into your own database schema. Quick way to do this: Go to the Operations tab, then find the "copy" database section, then **change the schema** to the one named after yourself, keep the same table name, and press "go". (Don't worry about the "adjust privileges" checkbox; yours will be greyed out.)

![copy table](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day5lab.1.png)

2. Now make a new table, called `sentiment140_dates` that has the same structure as `sentiment140_orig` but is empty (no data). Quick way to do this: Go to the Operations tab, then copy the table but choose "structure only", and rename the table. (Don't worry about the "adjust privileges" checkbox; yours will be greyed out.)

![copy structure only](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day5lab.2.png)

3. Use the Structure tab within the PhpMyAdmin interface to modify this new, empty `sentiment140_dates` table so that the `date_of_tweet` column is a `datetime` data type (rather than `varchar`). Look at the ALTER command that was run for you. Handy!

![alter data type](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day5lab.3.png)

4. Write a command that will ```INSERT``` all the rows from the `sentiment140_orig` table and put them into the `sentiment140_dates` table, except make sure that the new `date_of_tweet` column holds the correct data, formatted as a `datetime` data type yyyy-mm-dd hh:mm:ss. *Strive to do this in as few commands as possible.* When you are done, you should have data that looks like this: 

![cleaned dates](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day5lab.4.png)

5. Now create another *empty* version of the table (I called mine `sentiment140_char`) that has the same `datetime` column, but also add a column called `char_count` (an integer). This column will hold the count of characters present in the tweet. Come up with a procedure to ```INSERT``` all the data into this new table with *both* the cleaned dates and count of characters:

![cleaned dates and counted chars](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day5lab.5.png)

6. CHALLENGE: What domains are the most common in this data set? Write a query to extract domains and count them from the sentiment140_urls table.

![extracted URLs](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day5Lab.6.png)

## What to turn in
In Moodle, upload a text file with the commands you wrote for 4, 5, and 6.
