# Unit 5: Database Design
## 5.0 What is Database Design?
Up to this point in the semester most of our work has been to learn enough SQL to write queries to SELECT data out of the database, or occasionally to `INSERT` or `UPDATE` data.

With Database Design, we shift our focus away from querying the data in the database, and toward the creation of the tables themselves. The main tasks for Database Design are twofold: 

1. To build diagrams of the database, including the list of tables that should be in each table, what columns are in each table, and how the tables fit together;
1. To generate the associated SQL statements to CREATE the tables.

In relational database technology, we call the diagrams *Entity-Relationship diagrams*, or ERDs. You saw them already last week when we learned how to do `JOIN` in SQL. But as of yet, you have not made any of your own ERDs. That is the job of the Database Designer!

### 5.0.1 Where Does Database Design Fit In?
If you consider the overall world of databases, there are three main tasks:
* Database **developers** write queries and develop applications that use the data in the database.
* Database **designers** figure out which tables we need and what those tables should look like, how they connect. Database designers determine how to make a database and tables to fulfill particular business goals. They anticipate the design that will best fulfill the needs of the database developers.
* Database **administrators** set up users for the database and keep the machine itself healthy and running smoothly. They optimize queries, figures out hardware issues / bottlenecks. They also upgrade the software, applies patches and adjusts the configuration files, etc.

So far this semester we have been writing queries, which - according to that chart - makes us database developers, or database programmers.

### 5.0.2 Values of Database Design
Remember our list of Database Values from Unit 1. Our values as designers are are closely related to those, and we can modify them in this way:
* Our designs should strive for **efficiency**,
* Our designs should strive for **maintainability** into the future (we should plan ahead for growth and changes),
* Our designs should **reduce the possibility of error** in data entry, and
* Our designs should let the database do what it is good at. If the database can, within reason, support our business logic and rules, then we should take advantage of that. 
