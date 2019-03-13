## 5.3 Database Normalization
Database normalization is the process of making a relational database design that conforms to certain accepted best practices. Normalization best practices, when executed properly, will help us design a database with:
* less risk of duplicate data, and 
* more accurate data, and
* more atomic data.

### 5.3.1 First Normal Form
A table (relation) is in "first normal form" (1NF) when it meets two criteria: 
* There are no duplicate rows, and
* All values in the table should be atomic ("no multi-value attributes"). Relations in 1NF will be free of multi-value attributes, such as sets, inside of columns.

#### 1NF Example 1: phone numbers
Here is a relation that is NOT in 1NF (it violates the 2nd criterion about multi-value attributes). [Example from Wikipedia](https://en.wikipedia.org/wiki/First_normal_form)

![1nf violation 5.19](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.19.png)

How to fix and put the relation into 1NF:

![1nf violation 5.20](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.20.png)

Note that the relation does have unique rows, but they're just very duplicative. (We'll fix this with a higher normal form.)

#### 1NF Example 2: programming languages

![1nf violation 5.21](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.21.png)

#### 1NF Example 3: managers and workers

![1nf violation 5.22](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.22.png)

#### 1NF Example 4: dogs and owners

![1nf violation 5.44](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.44.png)

### 5.3.2 Second Normal Form (2NF)
A table is in second normal form (2NF) when it meets the definition of 1NF, plus, the following criterion:
* No column is dependent on only *part* of a candidate key. We sometimes say the table has "no partial functional dependencies".

What is a candidate key? A **candidate key** is any column that could be considered a valid primary key. 

The 2NF test makes us ask: Are there columns that are only dependent on part of the key? ("Dependent on" means that if one value changes, the other should too.) If so, then that table is NOT in 2NF.

> Special note: if a table has only one candidate key, and that candidate key is only comprised of a single column, then the table is automatically in 2NF. However, don't assume that every table with a single-column PK is in 2NF. If there were three columns that would have made a valid PK, but the table designer chose instead to add a synthetic key, then this table has a candidate key, and that means you still have to check it for 2NF violations!

Here is a drawing showing conceptually what a 2NF violation does. [image credit](http://www.virtualmv.com/wiki/index.php?title=DBMS:Normalisation) The blue rectangles are related to only part of the PK (the blue part). The solution is to split the blue rectangles out into their own table.

![2nf violation 5.23](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.23.png)

#### 5.3.2.1 2NF Example 1: teachers and rooms
The current PK is a composite key made up of `RoomNum` and `Block`. The `RoomPhoneNum` column is dependent only on the first column of the PK (`RoomNum`). Therefore, this table is NOT in 2NF.

![2nf violation 5.24](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.24.png)

The solution is to split rooms into their own table, remove `RoomPhoneNum` from this table. `RoomNum` can be a foreign key (column in common) back to the other table.

#### 5.3.2.2 2NF Example 2: electric toothbrushes and manufacturers
In this example, the `Manufacturer_Country` column is only dependent upon part of the PK: the `manufacturer` column. [image credit](https://www.slideshare.net/samyig/normal-forms-67127011)

![2nf violation 5.25](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.25.png)

The solution is to remove manufacturer information to its own table, and remove `country` from this table. `Manufacturer` can be a foreign key (column in common) back to that other table.  (BTW, the same problem exists with `model` and `model name`. Same solution applies.)

#### 5.3.2.3 2NF Example 3: yoga poses and playlists
In this example, we have a relation that has a synthetic primary key, called `ID`. However, there is also another candidate key, comprised of: `playlist_id`, `order`, `pose_id`. The table violates 2NF because `pose_name` is dependent on only one column of that candidate key (`pose_name` is dependent on `pose_id`).

![2nf violation 5.26](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.26.png)

### 5.3.3 Third Normal Form (3NF)
A table (relation) is in third normal form (3NF) when it meets the definition of 2NF, plus, the following criterion:
* No non-key column is dependent on any other non-key column. Sometimes we say the table has "no transitive functional dependencies".

The 3NF test makes us ask: Are there columns that are dependent on some other non-key column? ("Dependent on" means that if one value changes, the other should too.) If so, then that table is NOT in 3NF.

> Special note: if a table is in 2NF, and the table only has columns that comprise its PK, then the table/relation is automatically in 3NF. (Assuming the PK was made correctly.)

#### 5.3.3.1 3NF Example 1: members and companies
In the example below, `MID` is the PK for the member table. The `CompLoc` column is dependent upon `Company`, which is a non-key column. In this solution, they split out companies into their own joined table. They created a synthetic PK for Companies, which they used as a foreign key between itself and the `Member` table. [image credit](https://sakil2011.wordpress.com/2011/04/27/rules-of-data-normalization/)

![3nf violation 5.27](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.27.png)

#### 5.3.3.2 3NF Example 2: banks
In the example below, the PK is `ID`. The column called `bank` lists the names of the banks, and it is dependent on a non-key column (`bank_code_no`). To make this 3NF we have to split bank details out into their own table. [image credit](http://www.gitta.info/LogicModelin/en/html/DataConsiten_Norm3NF.html)

![3nf violation 5.28](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.28.png)

#### 5.3.3.3 Example
In the example below, the only two columns are `book_id` and `author_id`, and both columns comprise the PK (a composite PK). There are no other columns, and no other possible candidate keys. Therefore, this table is automatically in 3NF.

![3nf violation 5.29](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.29.png)
