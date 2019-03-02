# Day 10 Lab
## Goal
Use MySQL Workbench to design an Entity Relationship Diagram (ERD) for the following case. Save your diagram as a .pdf file and submit it.
## The Case
* Elon University has students who take courses taught by faculty members. Faculty members are part of departments. Each department has a name, an abbreviation, and a chairperson (who is also a faculty member).
* Each course has a title, a prefix (ex: CSC), a number (ex: 301), a number of semester hours (4 or 2, usually), and a section (A, B, etc), as well as a year and semester when the course was offered. Each time a student takes a course, the student gets a midterm letter grade and a final letter grade in each course. Grades are described by their letter and sign (A, A-, B+, B, etc) and a grade point associated with that (4.0, 3.0, and so on). Students can take a course (CSC 301) multiple times but may only take each *offering* of the course (CSC 301-A Spring 2019) once. 
* Courses can be taken by multiple students. Students can take multiple courses. Each section of a course is taught by a single professor (let's assume this for now, even though we know in real life courses can be "team-taught"). Faculty members may teach multiple courses.
## What to do
* Identify the "nouns" or "entities" that will become your tables.
* Identify the columns in the table, and choose a data type for each column. 
* Choose a primary key column, or set of columns, for the table. 
* Add the relationships between each table.
* Make sure the cardinalities correctly reflect the case as described.
* Save your diagram as a PDF file (File | Export | Single Page PDF) and upload it as today's lab. Save the .mwb file in a handy place (such as your own computer or on Google Drive) in case you need it later.
## What to turn in
* Save your diagram as a PDF file (File | Export | Single Page PDF) and upload it to Moodle as today's lab
