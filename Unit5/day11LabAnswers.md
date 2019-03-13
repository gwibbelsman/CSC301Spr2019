# Day 11 lab answers

## Question 1: Professor Lupin's Patronus Database

The trick with this one is realizing that a student can have more than one patronus (but only one AT A TIME). If the question had said that a student could only have one patronus in their life, then we could just put a patronusID column in the students table and skip the M:N junction table.

![q1.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q1.png)

## Question 2: Professor McGonagal's Human Transfiguration Database

This one is basically the same as the previous question, but it is worded differently.

![q2.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q2.png)

## Question 3: Professor Snape's Test Database

![q3.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q3.png)

## Question 4: Sorting Hat's Dormitory Database

Note that here, the headsOfHouse columns in the teachers table are all nullable.

![q4.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q4.png)

Here is an alternate partial diagram showing how to divide the teachers and heads of house into a 1:1 relationship. As described in [Unit 5.1 notes](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#step-4-adding-cardinalities-to-each-relationship), 1:1 relationships are very rare.

This diagram shows a 1:1 relationship where each teacher might be the head of one house, or might not be the head of any house.

![q4b.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q4b.png)
