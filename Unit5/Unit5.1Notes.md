## 5.1 Making Entity Relationship Diagrams
There are different notation styles you can use to make an ERD. We will be using one called a **crow's foot** notation.

Regardless of which ERD style you pick, they all show the same things:
* **Boxes**, representing the entities or tables
* **Lines**, representing the relationships between the tables

The lines connect the boxes to show which tables have a relationship with each other. 

### Step 1: Decide What Tables We Need
Each table represents one noun or one discrete idea. That's why tables are also called **entities**.

### Step 2: Add Columns and Select Primary Keys
After we decide what each table is about, we can begin adding the columns that describe that noun/entity.

Every table should have a **Primary Key** (PK). Up to this point in the course, we may have sometimes noticed Primary Keys while doing queries, but we have never really taken time to think about them in earnest.

#### Characteristics of Primary Keys: 
* the values are unique (all different), and
* the values are unchanging - pick to be the PK that can be permanent
* the values are easy-to-query (numbers are generally considered superior to strings, for example, and a 2-character string would be superior to a 25-character string)

#### Uniqueness of Primary Keys:
* A Primary Key is the "unique identifier" for each row in a table. 
* A PK could be a unique number that is given to each row
* A PK could be a unique word given to each row
* A PK could be a combination of two or more columns (Composite Key), as long as the *combination* of values in the columns is unique.

#### Primary Key vocabulary:
* A Primary Key can be either one column or multiple columns. Multiple-column primary keys are called **composite** keys.
* A Primary Key can be:
  * A new column created especially for this task. This is called a **synthetic key** or **surrogate key**.
  * One or more of the existing columns. This is called a **natural key**.
  * Composite keys can be either natural or synthetic.
* Primary Keys should ideally be given to every table at the time the table is created. It is a hassle to add them later because you have to `ALTER` the table, which can take a long time on a table with many rows.
* Primary Keys should also be **atomic** (indivisible) 

#### Utility of a Primary Key
* A Primary Key is "the best way" to identify a given record in a table. 
* Using the Primary Key is the fastest way to look up a record in a table. This is due to:
  * their uniqueness,
  * their short size, 
  * the fact that they are usually numbers, and 
  * the fact that they automatically get an "index" applied to them by the database software. (We will learn more about indexes in Unit 7)
* Using the Primary Key is the least likely column to cause confusion due to duplication - because Primary Key values are never duplicated.

#### Practice with Primary Keys
Below is an example of a simple, single column primary key.

![single column pk image 5.1](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.1.png)

Below is an example of a composite primary key. No one column is adequate to be the PK by itself, but a combination of the first two columns makes a good, unique PK.

![composite pk image 5.2](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.2.png)

##### Candidate Keys
**Candidate keys** are any columns (single column or set of columns) that are "in the running" to become the PK. Which columns would make good primary keys? There can be more than one candidate key per table. In the example below, the data shows that - at least right now - there are two candidate keys. *For the long term, which one would be the "better" choice for a PK?*

![candidate key image 5.3](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.3.png)

If you answered `StudentId`, I would agree with you. Why? 
1. The combination of `firstName` and `lastName` seems brittle - it could easily be violated in the future if another Jim Black or another Anne Norris enrolls. 
1. `StudentId` seems less likely to change - what if someone changes their name?
1. `StudentId` is shorter.

### Step 3: Add the Relationship Lines on an ERD
The lines on an ERD (generally) connect the primary keys in one table to some matching column(s) in the other table. We have seen this before when working on a `JOIN` query. With a `JOIN` query we saw how many times the column in common between two tables was made up of a PK in one table, matching to a non-key column in another table. 

> We call this non-key column that matches to a Primary Key in another table a **foreign key**.

Example:

![ERD image 5.4](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.4.png)

In this example, the column in common is `officeCode`. It is the primary key in the `offices` table, but it is NOT the primary key in the `employees` table. 

The lines where there is a key-to-nonkey relationship are called **foreign key relationships**. The **foreign key** is the key column from the related table. In this case `employees.officeCode` is a foreign key which points back to `offices.officeCode` which is the primary key of its table.

### Step 4: Adding Cardinalities to Each Relationship
In an ERD, there are also special symbols on the lines to indicate important facts about the relationship. These symbols tell us about the minimum and maximum **cardinality** of the relationship line. 

> Vocabulary tip: The word cardinality means "counting" or "how many". In database terms, cardinality means the same thing: How many of some entity am I allowed to have in this relationship?

Each end of the relationship line has a minimum and a maximum cardinality, for a total of FOUR cardinalities on each line. The boxes and lines and cardinalities together tell us which of three types of relationships the tables are in:
* One-to-Many (1:M) - these are the most common relationships
* Many-to-Many (M:N) - these will be decomposed into two 1:M relationships
* One-to-One (1:1) - very rare - do you really need this? 

> Note about one-to-one relationships. They are rare, and usually only used for the following cases:
> * When you have an area of the database you need to partition off, for example for security reasons. You would have had a table with 10 columns, but 3 of them are sensitive. Move the 3 columns into their own table, with security settings on it. Create a 1:1 relationship back to the main table. 
> * You have a very wide table and some of the columns "go together" logically and could safely be moved into their own table in order to make the main table more manageable.
> * You have a lot of nullable columns. Moving the columns out into a separate table with a 1:1 relationship means that you can remove sparse columns from your main table.

#### How to read cardinalities

![cardinality diagram 5.31.jpg](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.31.jpg)

[image credit](https://softwareengineering.stackexchange.com/questions/345709/erd-many-vs-zero-or-many-one-or-many-crowfoot-notation)

The cardinality pairing describes *how the data from one table will be found in the other table*. In other words, in the diagram below, the following are true:

* Any given `lecturer` can be found zero or many times in the `course` table. 
* Any given `lecturer` mentioned in the `course` table, has to be found back in the `lecturer` table once and only once.

![cardinality example 5.32.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.32.png)

[image credit](http://www.vertabelo.com/blog/technical-articles/crow-s-foot-notation)

It is fairly rare to have a 1-0 on the "parent" side of a relationship. However, below is a case where we *do* have a 0 on the parent side. This happens because `studentFaveColor` was set to be "nullable". Thus, every value for `studentFaveColor` won't be found in the `colors` table. (Because NULL is a possible value, and NULL won't be in the `colors` table.) Thus, we have to set a 0 for this cardinality. But this is fairly rare.

![Parent minimum 5.33.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.33.png)

### Step 5: Sanity Check (make sure the ERD makes sense in English)
This is the most important skill you can get from database design practice. Being able to read an ERD and tell what is - and is not - allowed is a very important skill.

#### Example 1: One-to-Many (1:M) relationship

![1:M example image 5.5](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.5.png)

How to read this in English: 
* An `office.officeCode` can appear in the `employees` table (in the `employees.officeCode` column) many times. 
* Every `office.officeCode` must appear at least once in the `employees` table.
* Each `employees.officeCode` must appear once and only once in the `offices` table.

#### Example 2: Multiple One-to-Many (1:M) relationships

![multiple 1:M relationships image 5.6](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.6.png)

How to read the top line in English: 
* A `posts.id` can appear in the `comments` table (in the `comments.post_id` column) many times. 
* Every `posts.id` must appear at least once in the `comments` table.
* Each `comments.post_id` must appear once and only once in the `posts` table.

How to read the bottom line in English: 
* A `users.id` can appear in the `posts` table (in the `posts.author_id` column) many times. 
* Every `users.id` must appear at least once in the `posts` table.
* Each `posts.author_id` must appear once and only once in the `users` table.

#### Example 3: Many-to-Many (M:N) relationship
![M:N relationships image 5.30](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.30.png)

How to read this diagram in English:
* An order can have 1 or many products on it = `orderID` can appear 1 or many times in the `OrderDetails` table
* A product can be ordered zero or many times = `productID` can appear zero or more times in the `OrderDetails` table 

#### Example 4: Many-to-Many (M:N) and One-to-Many (1:M) relationships
![M:N relationships image 5.7](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.7.png)

How to read this diagram in English:
* news can be written by at most one user (`author_id`) but users can write one or many news articles (but not zero).
* news can have one or more categories (but not zero)
* a category can have one or more news articles (but not zero)
* a news story can have one or multiple comments (but not zero ??)
* users can write one or multiple comments (but not zero)
