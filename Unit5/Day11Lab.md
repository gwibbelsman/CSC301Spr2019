# Day 11 lab: Practice with Database Design

## Goal
Practice creating database designs and associated ERDs, of varying levels of complexity.

## What to do
You have been hired by the Hogwarts School of Witchcraft and Wizardry as a Junior Database Designer. Create an ERD in MySQL Workbench for each of the following scenarios.

### Question 1: Professor Lupin's Patronus Database

Professor Lupin needs to keep track of students (name, school entry date, email, magical cell phone number), as well as what their ["patronus"](https://www.pottermore.com/features/what-is-a-patronus) is. 
* A patronus is a special animal shape that wizards can conjure as a form of protection, for example a patronus might take the shape of a deer or a turtle.) For each patronus, we need to track its description (dog, cat, etc) and a URL that points to a picture of the animal. 
* Multiple students can have the same patronus (for example, two students might both have a dog patronus). 
* Each student only has one patronus at a time, but may have multiple over their lifetimes. We want to keep track of this progression of students and patronuses (patroni?). 
* Sadly, some students never master the patronus charm, and thus these students do not have a patronus. Our database should support this situation as well.

Create an ERD showing a database design to support these requirements. Save it as a PDF file.

### Question 2: Professor McGonagall's Human Transfiguration Database

For this question, create a new data model.

Professor McGonagall teaches 6th year Hogwarts students how to transform themselves into animals in a class called "Human Transfiguration". There is a list of about 100 animals that McGonagal can teach the students to transform into, and each student can learn to transfigure into as many animals as they want to. Each student can try to learn how to transfigure into a particular animal, and when that animal is mastered, the student is allowed to move onto the next animal. Make sure you keep track of the date on which the student masters each transfiguration. 

Create an ERD showing a database design to support these requirements. Save it as a PDF file.

### Question 3: Professor Snape's Test Database

Professor Snape enjoys giving difficult tests and pop quizzes to his unfortunate <del>victims</del> students. Snape creates each test, giving it a name and a date that it will be administered. After creating each test, he begins to add questions to it. Because he is mean and a horrible teacher, the only type of questions that are allowed on the test are short answer questions. Each question has an order (question 1, question 2, and so on), the question text (For example, "What would I get if I added powdered root of asphodel to an infusion of wormwood?"), a number of points, and a correct answer.

Questions *can* be used on more than one test. For example, Snape is lazy so sometimes he asks the same question on a quiz, and then asks it later on the final exam.

Each student taking the test can answer each question only once. The student can leave an answer blank (null). Each answer needs to have a date and time (e.g. 2017-03-02 10:31:43) so Snape can see how long it took to answer each question.

Create an ERD showing a database design to support these requirements.

### Question 4: Sorting Hat's Dormitory Assignment Database

The students are assigned to dormitories (called ["Houses"](http://harrypotter.wikia.com/wiki/Hogwarts_Houses)) by the Sorting Hat. The database needs to track the assignment of Student to House, and what year that assignment occurred.

* The Sorting Hat needs to keep track of each student (name, email), each House (name, founder, colors, animal mascot, traits). 
* Every student has a house. 
* Every house has had at least one student in it. 
* Students can not be in more than one house.

The database should also keep track of the history of each "head of house" (the teacher that is assigned to be in charge of the house), as well as the dates (start date, end date) that the teacher was the head of house. Each teacher has a name, birthdate, and teaching specialty. Not every teacher is the head of a house. If the teacher IS the head of a house, they can only ever be the head of a single house.

In addition to the heads of houses, each house also has a number of students that are given special roles in the house. For example each house has a "Head Boy" and "Head Girl" and a number of student monitors, called "prefects".

Create an ERD showing a database design to support these requirements.

## What to turn in
Turn in a PDF file for each database design (File | Export | Single Page PDF). You will have up to 4 PDF files for this assignment.
