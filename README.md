# CSC 301, Database Systems Notes (Spring 2019)
## Megan Squire, Elon University

### Table of Contents
#### Unit 1: Introduction to Databases

* 1.0 [Basic concepts](https://github.com/megansquire/CSC301Spr2019/blob/master/Unit1/1.0Notes.md)
* 1.1 [Things we care about](https://github.com/megansquire/CSC301Spr2019/blob/master/Unit1/1.1Notes.md)
* 1.2 [Database vocabulary](https://github.com/megansquire/CSC301Spr2019/blob/master/Unit1/1.2Notes.md)
* 1.3 [Data types](https://github.com/megansquire/CSC301Spr2019/blob/master/Unit1/1.3Notes.md)
* 1.4 [Basic SQL commands](https://github.com/megansquire/CSC301Spr2019/blob/master/Unit1/1.4Notes.md)

<!--
#### Unit 2: SQL: SELECT
* 2.0 [Basic SELECT](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.0Notes.md)
* 2.1 [The WHERE clause](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.1Notes.md)
* 2.2 [Shortcuts to columns and tables: Aliases](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.2Notes.md)
* 2.3 [Sorting with ORDER BY](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.3Notes.md)
* 2.4 [Reducing results with LIMIT](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.4Notes.md)
* 2.5 [Creating sets with IN](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.5Notes.md)
* 2.6 Aggregating data
    - 2.6.0 [Simple aggregates](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.6.0Notes.md)
    - 2.6.1 [Aggregating with GROUP BY](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.6.1Notes.md)
    - 2.6.2 [Rules of GROUP BY](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.6.2Notes.md)
    - 2.6.3 [Efficiency](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.6.3Notes.md)
    - 2.6.4 [HAVING](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit2/2.6.4Notes.md)
-->
<!--
#### Unit 3: SQL: Functions and additional commands
* 3.0 [SQL Functions](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit3/3.0Notes.md)
* 3.1 [Date and time functions](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit3/3.1Notes.md)
* 3.2 [String functions](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit3/3.2Notes.md)
* 3.3 [Numeric functions](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit3/3.3Notes.md)
* 3.4 Additional SQL commands: [Data Manipulation](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit3/3.4Notes.md)
    - 3.4.0 SELECT
    - 3.4.1 INSERT
    - 3.4.2 INSERT-SELECT
    - 3.4.3 UPDATE
    - 3.4.4 DELETE
* 3.5 Additional SQL commands: [Data Definition](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit3/3.5Notes.md)
    - 3.5.0 CREATE
    - 3.5.1 DROP
    - 3.5.2 ALTER
    - 3.5.3 RENAME
-->
<!--
#### Unit 4: SQL: Joins and Subqueries
* 4.1 [What are joins for?](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.1Notes.md)
* 4.2 [INNER JOIN](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.2Notes.md)
    - 4.2.1 [Simple lookup table](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.2Notes.md#421-inner-join-example-simple-lookup-table)
    - 4.2.2 [Adding an Aggregate Function](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.2Notes.md#422-inner-join-example-2-adding-an-aggregate-function)
    - 4.2.3 [Selecting from Three+ Tables](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.2Notes.md#423-inner-join-example-3-selecting-from-three-tables)
    - 4.2.4 [Common JOIN Errors](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.2Notes.md#424-common-inner-join-errors)
    - 4.3.5 [Locating an ERD](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.2Notes.md#425-locating-your-erd) inside PhpMyAdmin
* 4.3 [OUTER JOIN](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.3Notes.md)
    - 4.3.1 [Simple Example](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.3Notes.md#431-outer-join-example-1-simple)
    - 4.3.2 [Adding an Aggregate Function](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.3Notes.md#432-outer-join-example-2-adding-an-aggregate)
* 4.4 [More Facts About JOINs](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.4Notes.md)
    - 4.4.1 [Equi-Join](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.4Notes.md#441-equi-join)
    - 4.4.2 [NATURAL JOIN](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.4Notes.md#442-natural-join)
    - 4.4.3 [Theta vs. ANSI Style](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.4Notes.md#443-theta-vs-ansi-style)
    - 4.4.4 [CROSS JOIN](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.4Notes.md#444-cross-join)
* 4.5 [Subqueries](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.5Notes.md)
    - 4.5.1 [Correlated vs. Non-Correlated](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.5Notes.md#451-correlated-vs-non-correlated-subqueries)
    - 4.5.2 [Things to know about Subqueries](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit4/Unit4.5Notes.md#452-things-to-know-about-subqueries)
-->
<!--
#### Unit 5: Database Design
* 5.0 [What is database design?](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.0Notes.md)
    - 5.0.1 [Where does database design fit in?](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.0Notes.md#501-where-does-database-design-fit-in)
    - 5.0.2 [Values of database design](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.0Notes.md#502-values-of-database-design)
* 5.1 [Entity-Relationship Diagrams](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md)
    - Step 1: [Decide what tables we need](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#step-1-decide-what-tables-we-need)
    - Step 2: [Add columns and select primary keys](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#step-2-add-columns-and-select-primary-keys)
        * [Characteristics of a primary key](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#characteristics-of-primary-keys)
        * [Uniqueness of a primary key](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#uniqueness-of-primary-keys)
        * [Primary key vocabulary](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#primary-key-vocabulary)
        * [Primary key utility](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#utility-of-a-primary-key)
        * [Practice with primary keys](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#practice-with-primary-keys)
        * [Candidate keys](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#candidate-keys)
    - Step 3: [Add relationship lines on ERD](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#step-3-add-the-relationship-lines-on-an-erd)
    - Step 4: [Add cardinalities to each relationship](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#step-4-adding-cardinalities-to-each-relationship)
    - Step 5: [Sanity-Check the ERD](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#step-5-sanity-check-make-sure-the-erd-makes-sense-in-english)
* 5.2 [Using MySQL Workbench for Database Design](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.2Notes.md)
    - 5.2.1 [Setting up MySQL Workbench](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.2Notes.md#521-setting-up-mysql-workbench)
    - 5.2.2 [Using MySQL Workbench to create ERDs](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.2Notes.md#522-using-mysql-workbench-to-create-erds)
    - 5.2.3 [Forward-Engineering ERDs](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.2Notes.md#523-using-mysql-workbench-to-forward-engineer-an-erd)
* 5.3 [Database Normalization](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.3Notes.md)
* 5.4 [Indexes](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.4Notes.md)
* 5.5 [Views](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.5Notes.md)
    - 5.5.1 [What are views?](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.5Notes.md#551-what-are-views)
    - 5.5.2 [Why are views useful?](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.5Notes.md#552-why-are-views-useful)
    - 5.5.3 [The downsides and limitations of using views](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.5Notes.md#553-what-are-the-downsides-to-using-a-view)
    - 5.5.4 [Updating data in a view](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.5Notes.md#554-updating-data-in-a-view)
    - 5.5.5 [Setting up views in PhpMyAdmin](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.5Notes.md#555-setting-up-views-in-phpmyadmin)
* 5.6 [Metadata & Charsets](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.6Notes.md)
    - 5.6.1 [What is metadata?](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.6Notes.md#561-what-is-metadata)
    - 5.6.2 [MySQL's Information Schema](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.6Notes.md#562-mysqls-information_schema)
    - 5.6.3 [MySQL Storage Engines](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.6Notes.md#563-mysql-storage-engines)
    - 5.6.4 [Database character sets and collations](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.6Notes.md#564-database-character-sets-and-collations)
-->
<!--
#### Unit 6: Database programming in Python
* 6.1 [Getting ready and installing Python](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit6/Unit6.1Notes.md)
* 6.2 [Writing a basic database program](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit6/Unit6.2Notes.md)
* 6.3 [Writing programs with dynamic queries](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit6/Unit6.3Notes.md)
* 6.4 [Writing a program to modify the database](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit6/Unit6.4Notes.md)
* 6.5 [Python and SQL string processing](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit6/Unit6.5Notes.md)
* 6.6 [Python regular expressions](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit6/Unit6.6Notes.md)
* 6.7 [SQL regular expressions](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit6/Unit6.7Notes.md)
-->
<!--
#### Unit 7: JSON, No-SQL, document databases, MongoDB
* 7.1 [Intro to JSON and Document Databases](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit7/Unit7.1Notes.md)
* 7.2 [MySQL's Implementation of JSON](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit7/Unit7.2Notes.md)
* 7.3 [Working with JSON in Python](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit7/Unit7.3Notes.md)
* 7.4 [Intro to MongoDB and Document Databases](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit7/Unit7.4Notes.md)
* 7.5 [Connecting to MongoDB via Python](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit7/Unit7.5Notes.md)
-->
