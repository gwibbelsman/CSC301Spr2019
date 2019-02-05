# Day 1 Lab
## Purpose
Get familiar with PhpMyAdmin, create a simple table, insert some data, make changes to the table and the data inside the table. Apply concepts from Unit 1.

## What to do
### 0. Open the Day 1 Moodle answer and be ready to type in answers to questions 5, 6, 7 below.

### 1. Log into the server 
I've set each of you up with a user account on the [Grid8 CS database server](http://grid8.cs.elon.edu/phpmyadmin/). Log in.

### 2. Click into your database schema
On the left-hand pane, click into the database schema named after yourself. This is where you will do your work.

### 3. Create a new table 
* Assume you are a veterinarian. The following SQL `CREATE` statement has been run for you to create your pets table: 
```sql
CREATE TABLE `pets` (
  `petID` int(11) NOT NULL PRIMARY KEY,
  `petName` varchar(30) NOT NULL,
  `birthdate` date DEFAULT NULL,
  `petType` enum('cat','chicken','dog','fish','reptile') NOT NULL,
  `ownerFirst` varchar(30) NOT NULL,
  `ownerLast` varchar(30) NOT NULL,
  `sex` enum('m','f','unknown') DEFAULT NULL,
  `lastVisitDate` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `notes` text
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```
* The table has the following characteristics:
  * petID: this is a special number that refers to the pet individually 
  * petName: this is the pet's name, for example Fifi or Snuffles, 
  * birthdate (month, day, and year), 
  * petType (the only available choices are cat, dog, fish, reptile, chicken), 
  * Owner's first and last name, 
  * sex (for a dog or cat this can be 'm' or 'f', but what do we do about fish - it might be hard to tell! Should we have an "unknown" column?), 
  * The date of the pet's last visit, and 
  * A free-typing 'notes' field.
  * Some of the columns are allowed to be 'nullable'. 
  * `petId` is set to be the Primary Key, or unique identifier, for rows in this table. This means no two pets can have the same ID number.

### 4. INSERT  data
* Now we need to add pets to the table.
* Use the PhpMyAdmin `INSERT` tab to insert 10 pets (10 rows of data) to your table.
* Make sure you add at least one chicken with sex 'unknown'
* Make sure you add at least one dog.

### 5. UPDATE data
* Oh no, the chicken just revealed itself to be a rooster. Use the "Edit" button to construct an `UPDATE` statement to change that chicken's sex from 'unknown' to 'm', and update it so that today's date is the last visit. 
* If possible, copy this `UPDATE` statement to your Moodle window. 

### 6. Modify your table. 
* Tragedy strikes: One of the dogs died. What is the best way to reflect its untimely demise in the database? (Assume that you want to keep a record that the pet was once a patient, so you don't want to DELETE it entirely.) 
  * On the 'Structure' tab, add a new column to your table that indicates whether the pet is "deceased" or not. There are a few different ways to reflect this information. 
  * Copy the `ALTER` statement that PhpMyAdmin constructed for you into your text file. 
* Now `UPDATE` that pet's record to show the fact that it died. 
  * Copy the `UPDATE` statement(s) to your text file (if possible).

## What to turn in
Paste in your SQL statements for 5 nd 6 into the Moodle `day1` assignment box (save the file somewhere too, if you like). If you didn't finish today, keep working on these on your own time so you won't be behind for future classes.
