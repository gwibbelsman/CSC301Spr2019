# Day 1 lab answers

* Here is the SQL `CREATE` statement that made the `pets` table that was constructed for you:
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
* Add some Pets to the table. 
Here are a few sample `INSERT` statements. You probably used the GUI's "insert tab" to make these, but here is what the SQL looked like:
```sql
INSERT INTO `pets` (`petID`, `petName`, `birthdate`, `petType`, `ownerFirst`, `ownerLast`, `sex`, `lastVisitDate`, `notes`) VALUES
(1, 'Suzie', '2017-09-03', 'cat', 'Tom', 'Jones', 'f', '2017-09-03 12:58:56', NULL),
(2, 'Murphy', '2017-09-04', 'dog', 'Sally', 'Smith', 'f', '2017-09-03 12:59:25', 'nothing much to say about this pet.'),
(3, 'PiedPiper', NULL, 'fish', 'Dinesh', 'Gilfoyle', 'unknown', '2017-09-03 13:00:14', NULL),
(4, 'Funny Beak', NULL, 'chicken', 'Kurt', 'Cobain', 'unknown', '2017-08-10 14:45:16', NULL);
```
* Here is the `UPDATE` statement that was made when you changed the sex of one of the pets: 
```sql
UPDATE `pets` SET `sex` = 'm' WHERE `pets`.`petID` = 4;
```
* Here is the `ALTER` statement that was run to add the option of a deceased pet:
```sql
ALTER TABLE `pets` ADD `deathDate` DATE;
```
* Here is the SQL that was run when we killed pet #3
```sql
UPDATE `pets` SET `deathDate` = '2018-01-31' WHERE `pets`.`petID` = 3;
```
