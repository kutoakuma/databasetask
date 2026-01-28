# databasetask
# Introduction
## SCHEMAS
### Majors(Major,Advisor)
## SQLQUERY:
~~~
CREATE TABLE Majors (
Major VARCHAR(50) PRIMARY KEY,
Advisor VARCHAR(100) NOT NULL
);
~~~
## Table Description
~~~
describe Majors;
~~~
## Result
~~~
+---------+--------------+------+-----+---------+-------+
| Field   | Type         | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+-------+
| Major   | varchar(50)  | NO   | PRI | NULL    |       |
| Advisor | varchar(100) | NO   |     | NULL    |       |
+---------+--------------+------+-----+---------+-------+
~~~
## Students table (StudentID, Name, Email, Major)
### SQLQUERY
~~~
CREATE TABLE Students (
StudentID VARCHAR(10) PRIMARY KEY,
Name VARCHAR(100) NOT NULL,
Email VARCHAR(100) UNIQUE NOT NULL,
Major VARCHAR(50),
FOREIGN KEY (Major) REFERENCES Majors(
Major)
~~~
## Table description
~~~
describe Students;
~~~
## Result
~~~
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| StudentID | varchar(10)  | NO   | PRI | NULL    |       |
| Name      | varchar(100) | NO   |     | NULL    |       |
| Email     | varchar(100) | NO   | UNI | NULL    |       |
| Major     | varchar(50)  | YES  | MUL | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
~~~
## Courses (CourseID, CourseTitle, Credits, Building, Room)
### SQLQUERY
~~~
CREATE TABLE Courses ( CourseID VARCHAR(10) PRIMARY KEY, 
CourseTitle VARCHAR(100) NOT NULL, 
Credits INT NOT NULL, 
Building VARCHAR(50), 
Room VARCHAR(10) ); 
~~~
## Table description
~~~
describe Courses;
~~~
## Result
~~~
+-------------+--------------+------+-----+---------+-------+
| Field       | Type         | Null | Key | Default | Extra |
+-------------+--------------+------+-----+---------+-------+
| CourseID    | varchar(10)  | NO   | PRI | NULL    |       |
| CourseTitle | varchar(100) | NO   |     | NULL    |       |
| Credits     | int          | NO   |     | NULL    |       |
| Building    | varchar(50)  | YES  |     | NULL    |       |
| Room        | varchar(10)  | YES  |     | NULL    |       |
+-------------+--------------+------+-----+---------+-------+
~~~
## Enrollments (StudentID, CourseID, Grade)
### SQLQUERY
~~~
CREATE TABLE Enrollments ( StudentID VARCHAR(10), 
CourseID VARCHAR(10), 
Grade CHAR(1), 
PRIMARY KEY (StudentID, CourseID), 
FOREIGN KEY (StudentID) REFERENCES Students(StudentID), 
FOREIGN KEY (CourseID) REFERENCES Courses( CourseID) );
~~~
## Table description
~~~
describe Enrollments;
~~~
## Result
~~~
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| StudentID | varchar(10) | NO   | PRI | NULL    |       |
| CourseID  | varchar(10) | NO   | PRI | NULL    |       |
| Grade     | char(1)     | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
~~~
## Inserting the sample value
~~~
INSERT INTO Majors VALUES
('CS', 'Dr. Smith'),
('Physics', 'Dr. Lee');

INSERT INTO Students VALUES
('S101', 'Alice', 'alice@uni.edu', 'CS'),
('S102', 'Bob', 'bob@uni.edu', 'CS'),
('S103', 'Carol', 'carol@uni.edu', 'Physics');

INSERT INTO Courses VALUES
('CS301', 'Algorithms', 4, 'Science', '205'),
('MATH201', 'Linear Algebra', 3, 'Math Wing', '101'),
('PHYS101', 'Mechanics', 4, 'Science', '301');

INSERT INTO Enrollments VALUES
('S101', 'CS301', 'A'),
('S101', 'MATH201', 'B'),
('S102', 'CS301', 'C'),
('S103', 'PHYS101', 'A');
~~~
### TO display the table
~~~
SELECT * FROM Majors;
SELECT * FROM Students;
SELECT * FROM Courses;
SELECT * FROM Enrollments;
~~~
### Result
~~~
+---------+-----------+
| Major   | Advisor   |
+---------+-----------+
| CS      | Dr. Smith |
| Physics | Dr. Lee   |
+---------+-----------+

+-----------+-------+---------------+---------+
| StudentID | Name  | Email         | Major   |
+-----------+-------+---------------+---------+
| S101      | Alice | alice@uni.edu | CS      |
| S102      | Bob   | bob@uni.edu   | CS      |
| S103      | Carol | carol@uni.edu | Physics |
+-----------+-------+---------------+---------+


+----------+----------------+---------+-----------+------+
| CourseID | CourseTitle    | Credits | Building  | Room |
+----------+----------------+---------+-----------+------+
| CS301    | Algorithms     |       4 | Science   | 205  |
| MATH201  | Linear Algebra |       3 | Math Wing | 101  |
| PHYS101  | Mechanics      |       4 | Science   | 301  |
+----------+----------------+---------+-----------+------+

+-----------+----------+-------+
| StudentID | CourseID | Grade |
+-----------+----------+-------+
| S101      | CS301    | A     |
| S101      | MATH201  | B     |
| S102      | CS301    | C     |
| S103      | PHYS101  | A     |
+-----------+----------+-------+
~~~
