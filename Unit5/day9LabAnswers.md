# Day 9 lab answers

[day 9 answer PDF](https://github.com/megansquire/CSC301Spr2019/blob/master/images/9.pdf)

## States and Students
In the first question, a given state code can be represented in the students table 0 or many times. Each student must have a state listed that is found in the states table 1 and only 1 time. In this scenario, states is the parent or lookup table, and students is the "child" table.

## Dogs and Owners
In the second question, each owner can have 1 or multiple dogs. Each dog has to have an owner that is listed in the owners table 1 and only 1 time. Between these two tables, owners is the lookup/parent table, and dogs is the child table.

## Books and Authors
In the third question we need a many to many relationship between books and authors. A given book can have 1 or multiple authors, and a given author can write 1 or multiple books. We decompose this M:N relationship into two 1:M relationships. The central table, or "junction table" is named after the two parent tables (Books and Authors makes a table called book_authors, for example) and the PK in that table becomes a composite PK of the PKs from the two parent tables.

## Twitter Users & followers
For this question, we create two 1:M relationships between twitter users and followers. A user can be in the followers table many times, both as a follower and a followee. Options for primary key include: (1) A composite primary key made up of the twitter user id and the followee id, with foreign keys back to the TwitterUsers table. (2) A synthetic primary key for the relationship, and two foreign keys back the the followers table.
