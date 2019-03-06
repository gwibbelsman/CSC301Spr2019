## 5.2 Using MySQL Workbench for Database Design
MySQL Workbench is just another front-end **client** into a MySQL database, just like PhpMyAdmin (PMA) is a front-end client into a MySQL database. The main difference between Workbench and PMA is that Workbench is a full desktop application, but PMA is just a web app that runs in a web browser.

MySQL Workbench is pre-loaded on the lab computers, but you can also [download it for your own machine](https://www.mysql.com/products/workbench/) if you like.

### 5.2.1 Setting up MySQL Workbench
The first step in using MYSQL Workbench is to set up a connection to some existing database. 

* Connection name. You can name it whatever you like.
* Hostname. This is the name of the machine you are connecting to
* Username. Your account name (the same thing you type when you log into PMA)
* Password. You will be prompted to enter your database password (the same one you type when you log into PMA)

Here is the way the completed login form should look:
![mysql workbench setup image 5.8](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.8.png)

### 5.2.2 Using MySQL Workbench to Create ERDs
To begin making an ERD, use `File | New Model`, then select the ERD icon at the top of the screen. The abbreviation "EER" stands for Extended Entity Relationship Diagram, and it is roughly synonymous with ERD.

![mysql workbench EER 5.9](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.9.png)

To begin adding tables and relationships, use the "table" icon on the toolbar. Then add all your columns, and set the data type for each. Finally, create the relationships using the icon that looks like an eyedropper with a 1:n symbol next to it.

![mysql workbench erd 5.10](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.10.png)

Add or fix the cardinalities to each relationship line by using the screen below. To see this screen, double-click the table or relationship line you are interested in.

![mysql workbench erd 5.11](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.11.png)

Attention Mac users: There is a known MySQL Workbench bug that makes your PK "key" symbols disappear sometimes. When you create a composite primary key that then becomes a foreign key back to another table, sometimes the keys are made correctly, but the key icons disappear from the ERD. [Here is a description of the bug](https://bugs.mysql.com/bug.php?id=81482&error=lp).

### 5.2.3 Using MySQL Workbench to Forward-Engineer an ERD
After your model (ERD) is made, it is time to auto-generate the `CREATE` statements so we can build the model out on the database server.

First, we have to tell MySQL Workbench which database schema is ours on the server. From the MySQL Model tab, locate the default `mydb` schema and Edit it so that it points to the correct database. (At Elon, this will be the CS server database schema named after yourself.)

![mysql workbench menu 5.12](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.12.png)

![mysql workbench mydb edit 5.13](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.13.png)

Next, we will decide how we want to make the tables on the database server. 
* Option 1: we can generate a .sql file to hold our `CREATE` statements and manually run that on our database server, or 
* Option 2: we can connect directly from Workbench to the database server and execute the `CREATE`s from within Workbench.

> SPECIAL NOTE FOR MYSQL Workbench version 8:
> Sometimes the script generator adds the keyword "VISIBLE" into the .sql script. You will need to remove this keyword in order to make the CREATE statements work properly.

#### Create the tables using PhpMyAdmin

From the MySQL Workbench File menu, choose Export | Forward Engineer SQL CREATE Script.

![workbench forward engineer 5.14](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.14.png)

Save the CREATE script to a new filename if you want to save it (a good idea).

![workbench forward engineer 5.15](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.15.png)

You can select all or some of the tables on the ERD. Use the filter button if you don't want to export all the tables:

![workbench filter 5.16](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.16.png)

Check the script to make sure that your database schema is set correctly (not `mydb`), and that the tables look good.

> SPECIAL NOTE FOR MYSQL Workbench version 8:
> Sometimes the script generator adds the keyword "VISIBLE" into the .sql script. You will need to remove this keyword in order to make the CREATE statements work properly.

![workbench generated script 5.17](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.17.png)

Open the file you created and copy out the SQL for the tables. Paste the code into a PhpMyAdmin SQL tab:

![paste script into pma 5.18](https://github.com/megansquire/CSC301Spr2019/blob/master/images/5.18.png)

> SPECIAL NOTE FOR MYSQL Workbench version 8:
> Sometimes the script generator adds the keyword "VISIBLE" into the .sql script. You will need to remove this keyword in order to make the CREATE statements work properly.
