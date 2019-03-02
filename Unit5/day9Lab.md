# Day 9 lab
## Goal
Practice creating simple ERDs on paper

## What to do
On paper, create tiny ERDs for the following scenarios. Each table in the ERD should have all columns as specified, as well as a PK identified. Draw lines between the tables. Draw the cardinalities that match the description given. Next to each table, list a few "sample" rows of data.

### 1- Students and states. 
Create a table of students and what state they are from. 
* Students have a first & last name, address (street, city, state, zip), email, phone. 
* States have an abbreviation/code and a name (ex: NC and North Carolina). 
* Each student lives in at most one state. 
* Some states have no students living in them. Other states can have multiple students living in them. 
* You can give each student a number for a primary key, if you like.

For each table, list a few rows of sample data.

### 2- Dogs & owners. 
Create a data model for dog ownership. 
* Each dog has a unique number, a first name, a last name, an approx birth year, and a description. 
* Every dog also has one owner. Owners have the typical contact info (unique id number, name, address, phone, email). 
* An owner might have multiple dogs. 
* Let's assume for this example, every owner has to have at least one dog.

For each table, list a few rows of sample data.

### 3- Books and authors.
Create a data model describing book authorship. 
* Authors have the typical contact info (unique identifier, name, birthdate, web site, email). 
* Books have a *unique* 13-digit ISBN number, title, and price. 
* Each book can have one or more authors. 
* An author will write one or more books. 

For each table, list a few rows of sample data.

### 4- Twitter users and followers
Create a data model describing Twitter.
* Twitter users have information about them (id number, username, display name, profile picture URL). 
* Each Twitter user can follow 0 or more other users. Follow relationships are *not* bi-directional. (In other words, you can follow someone and they don't have to follow you back.)

For each table, list a few rows of sample data.

## What to turn in
Turn in your paper with your name at the top.
