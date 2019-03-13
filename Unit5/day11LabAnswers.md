# Day 11 lab answers

## Question 1: Professor Lupin's Patronus Database

The trick with this one is realizing that a student can have more than one patronus (but only one AT A TIME). If the question had said that a student could only have one patronus in their life, then we could just put a patronusID column in the students table and skip the M:N junction table.

![q1.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q1.png)

> Another way to do the junction table here would be to NOT have a composite key, but instead create a synthetic key, then just have the two parent columns-in-common (student_id and patronus_id) as foreign keys back to their respective parent tables. In such a version of the diagram, the two parent tables stay exactly the same. 

## Question 2: Professor McGonagal's Human Transfiguration Database

This one is basically the same as the previous question, but it is worded differently.

![q2.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q2.png)

> Another way to do the junction table here would be to NOT have a composite key, but instead create a synthetic key, then just have the two parent columns-in-common (student_id and animal_id) as foreign keys back to their respective parent tables. In such a version of the diagram, the two parent tables stay exactly the same.

## Question 3: Professor Snape's Test Database

![q3.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q3.png)
> Here we have three basic nouns: students, tests, and questions. A test can have many questions, and a question can be on many tests, so we create a junction table (test_questions) to support this M:N relationship. The relationship between students and test_questions is similar. A student can answer many test_questions, and each test_question can be answered by many students, thus a junction table is created to store these. The PK of this table is the unique combination of a student, test, and question.

## Question 4: Sorting Hat's Dormitory Database

In the diagram below, the headsOfHouse columns in the teachers table are all nullable.

![q4a.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q4a.png)

Here is an alternate partial diagram showing how to divide the teachers and heads of house into a 1:1 relationship. As described in [Unit 5.1 notes](https://github.com/megansquire/CSC301Fall2018/blob/master/Unit5/Unit5.1Notes.md#step-4-adding-cardinalities-to-each-relationship), 1:1 relationships are very rare.

This diagram shows a 1:1 relationship where each teacher might be the head of one house, or might not be the head of any house.

![q4b.png](https://github.com/megansquire/CSC301Spr2019/blob/master/images/hogwarts.q4b.png)
