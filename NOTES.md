# MY NOTES ON SQL

CREATE DATABASE College;

USE College;

CREATE TABLE studentstudent(
 id int primary key,
 name varchar(30),
 age int not null
);

INSERT INTO student values(1, "LUFFY", 19);

INSERT INTO student values(2, "ZORO", 21);

INSERT INTO student values(3, "SANJI", 22);

SELECT * FROM student;

-- --------------------------------------------------------------

-- IF NOT EXISTS--

CREATE DATABASE IF NOT exists College;


-- DROP / IF EXISTS

DROP DATABASE IF EXISTS D2;


-- DISPLAYS ALL THE DATABASES--

SHOW DATABASES;


-- DISPLAYS ALL THE TABLES IN THE SELECTED DATABASE--

SHOW TABLES;


-- DELETES THE TABLE FROM THE DATABASE--

DROP TABLE student;

-- --------------------------------------------------------

CREATE DATABASE employee;

USE employee;

CREATE TABLE Info(
 Id INT PRIMARY KEY,
 Name VARCHAR(40),
 Salary INT NOT NULL
);

INSERT INTO Info values(1, "Peter Quill" , 10000);

INSERT INTO Info values(2, "Drax" , 10000);

INSERT INTO Info values(3, "Rocket" , 10000);

Select * from Info;

INSERT INTO Info values(4, "Groot" , 10000),

(5, "Mantis" , 10000),(6, "Gamora" , 10000);

-- -----------------------------------------------------

CREATE DATABASE IF NOT EXISTS XYZ;

USE XYZ;

CREATE TABLE EMPLOYEE_INFO(
 ID INT PRIMARY KEY,
 NAME VARCHAR(30),
 SALARY INT NOT NULL
);

INSERT INTO EMPLOYEE_INFO values(1, "ADAM" , 25000),

(2, "BOB" , 30000),(6, "CASEY" , 40000);

SELECT * FROM  EMPLOYEE_INFO;


-- UPDATE

UPDATE EMPLOYEE_INFO SET ID = 3 WHERE ID = 6;

-- ------------------------------------------------------

CREATE TABLE ID(
 ID INT UNIQUE
);

INSERT INTO ID VALUES (100);

INSERT INTO ID VALUES (101);

SELECT * FROM ID;

-- ------------------------------------------------------

CREATE TABLE EMP(
 ID INT,
 NAME VARCHAR(30),
 age INT,
 city VARCHAR(30),
 PRIMARY KEY(ID,age)
);

INSERT INTO EMP VALUES (100 ,"A", 23, "pune");

INSERT INTO EMP VALUES (101 ,"A", 24, "delhi");

INSERT INTO EMP VALUES (101 ,"B", 23, "delhi");

SELECT * FROM EMP;

-- ---------------------------------------------------

use luffy;

create table pirates(
  id int,
  ship varchar(20) default "Going Merry"
);

insert into pirates values(1,"Thousand Sunny"); 

insert into pirates (id) values (2); 

select * from pirates;

-- ---------------------------------------------------

USE college;

CREATE TABLE stud(
id INT PRIMARY KEY,
 Name Varchar(30),
 age INT,
 city Varchar(20),
 CONSTRAINT age_check CHECK (age <= 18  AND city = "Delhi")
);

INSERT INTO stud VALUES(1, "A", 18, "Delhi");

INSERT INTO stud VALUES(2, "B", 18, "Delhi");

INSERT INTO stud VALUES(3, "C", 16, "Delhi");

INSERT INTO stud VALUES(4, "D", 16, "Delhi");

INSERT INTO stud VALUES(5, "E", 17, "Delhi");

SELECT * FROM stud;

-- ------------------------------------------------------------

CREATE DATABASE IF NOT EXISTS College;

USE College;

CREATE TABLE student (
 roll_no INT PRIMARY KEY,
 name VARCHAR(30),
 marks INT NOT NULL,
 grade VARCHAR(1),
 city VARCHAR(20)
 );
 
 INSERT INTO student VALUES(101, "Anil", 78, "C", "Pune");
 
 INSERT INTO student VALUES(102, "Bhumika", 93, "A", "Mumbai");
 
 INSERT INTO student VALUES(103, "Chetan", 85, "B", "Mumbai");
 
 INSERT INTO student VALUES(104, "Dhruv", 96, "A", "Delhi");
 
 INSERT INTO student VALUES(105, "Emanuel", 12, "F", "Delhi");
 
 INSERT INTO student VALUES(106, "Farah", 82, "B", "Delhi");

 
-- It can also be written in this way->

--  INSERT INTO student (roll_no, name, marks, grade, city)  VALUES 

--  (101, "Anil", 78, "C", "Pune");

--  (102, "Bhumika", 93, "A", "Mumbai");

--  (103, "Chetan", 85, "B", "Mumbai");

--  (104, "Dhruv", 96, "A", "Delhi");

--  (105, "Emanuel", 12, "F", "Delhi");

--  (106, "Farah", 82, "B", "Delhi");


-- ALTER TABLE

-- ADD COLUMN

ALTER TABLE student ADD COLUMN age INT NOT NULL DEFAULT 18;

-- DROP COLUMN

ALTER TABLE student DROP COLUMN age;

-- RENAME TABLE

ALTER TABLE student RENAME TO students;

ALTER TABLE students RENAME TO student;

-- CHANGE COLUMN (name)

ALTER TABLE student CHANGE COLUMN roll_no rollno INT ;

-- MODIFY COLUMN (datatype and constrains)

ALTER TABLE student MODIFY COLUMN marks FLOAT NOT NULL;

ALTER TABLE student MODIFY COLUMN marks INT NOT NULL;

SELECT * FROM student;

SELECT name, marks, grade FROM student;

-- UPDATE DATA

-- to off the safe mode we use

SET SQL_SAFE_UPDATES = 0;  -- 0 to off 1 to on

UPDATE student SET marks = 82 WHERE marks = 12;
 
UPDATE student SET grade = "B" WHERE marks BETWEEN 80 AND 90;

-- to increase the marks of every student by +1

UPDATE student SET marks = marks+1;

UPDATE student SET marks = 12 WHERE name = 105;

-- DELETE 

DELETE FROM student WHERE marks < 70; 

-- be careful using DELETE because we can easily lose our precious data

-- DELETE FROM student can delete the whole table 

-- DISTINCT KEYWORD --

SELECT DISTINCT city FROM student;

-- WHERE

SELECT name, marks, grade FROM student WHERE marks >= 80;

SELECT * 
FROM student 
WHERE city = "Mumbai" ;

-- AND / BETWEEN / WHERE

SELECT name, marks, grade FROM student WHERE city = "Delhi" AND  marks BETWEEN 50 AND 100;

-- BETWEEN 

SELECT name, marks, grade FROM student WHERE marks BETWEEN 50 AND 100;

-- +

SELECT * FROM student WHERE marks +10 > 100;  

-- %

SELECT name FROM student WHERE rollno = marks % 2 = 0;

-- > / AND

SELECT * FROM student WHERE marks > 80 AND city = "Mumbai" ;

-- > / OR

SELECT * FROM student WHERE marks > 80 OR city = "Mumbai" ;

-- IN 

SELECT * FROM student WHERE city IN ("Mumbai") ;

SELECT * FROM student WHERE city IN ("Mumbai", "Delhi") ;

-- NOT IN 

SELECT * FROM student WHERE city NOT IN ("Mumbai", "Delhi") ;

-- the cities are not in database so it will print an empty table

SELECT * FROM student WHERE city IN ("Kolkata", "Haryana") ;

-- LIMIT

SELECT * FROM student LIMIT 3;

SELECT * FROM student WHERE marks > 80 LIMIT 3;

SELECT name , grade FROM student WHERE marks > 80 LIMIT 3;

-- ORDER BY / default is ASC

SELECT * FROM student ORDER BY city; 

SELECT * FROM student ORDER BY city ASC;

SELECT * FROM student ORDER BY marks DESC;

-- In this way we can find the top 3 students in the class

SELECT * FROM student ORDER BY marks DESC LIMIT 3;


-- AGGREGATE FUNCTIONS

-- MAX()

SELECT MAX(marks) FROM student;

-- MIN()

SELECT MIN(marks) FROM student;

-- SUM()

SELECT SUM(marks) FROM student;

-- AVG()

SELECT AVG(marks) FROM student;

-- COUNT()
SELECT COUNT(roll_no) FROM student;

-- GROUP BY()
SELECT city FROM student GROUP BY city; 

-- GROUP BY() / COUNT()

SELECT city, COUNT(name) FROM student GROUP BY city; 

-- it will throw an error because we need to include roll_no in group by

-- SELECT city, roll_no, COUNT(name) FROM student GROUP BY city; 

 SELECT city, roll_no, COUNT(name) FROM student GROUP BY city , roll_no; 
 
 SELECT city, AVG(marks) FROM student GROUP BY city; 
 
 SELECT city, MAX(marks) FROM student GROUP BY city; 

-- PRACTISE QUERY- Query to find avg marks in each city in ascending order --

SELECT city, AVG(marks) FROM student GROUP BY city ORDER BY avg(marks) ;

SELECT city, AVG(marks) FROM student GROUP BY city ORDER BY city DESC ;

SELECT grade, COUNT(name) FROM student GROUP BY grade;

SELECT grade, COUNT(name) FROM student GROUP BY grade ORDER BY grade ASC;

-- HAVING

-- To count the no of students in each city where marks is more than 90.

SELECT city, COUNT(name) FROM student GROUP BY city Having MAX(marks) > 90;  

-- this will print the city marks and no of students who has marks more than 90. 

SELECT city, COUNT(name), marks FROM student GROUP BY city, marks Having MAX(marks) > 90;

-- this will cause an error of invalid use group function

-- SELECT city, COUNT(name) FROM student WHERE MAX(marks) > 90 GROUP BY city;

-- GENERAL ORDER
SELECT city
FROM student
WHERE grade = "A"
GROUP BY city
HAVING MAX(marks) >= 93
ORDER BY city DESC;

-- -----------------------------------------------------------------------------------------

CREATE DATABASE IF NOT EXISTS employee;

USE employee;

CREATE TABLE PAYMENT(
 customer_id INT PRIMARY KEY,
 customer VARCHAR(30),
 mode VARCHAR(20),
 city VARCHAR(20)
);

INSERT INTO PAYMENT (customer_id, customer, mode, city) VALUES

 (101, "Olivia Barrett", "Netbanking", "Portland"),
 
 (102, "Ethan Sinclair", "Credit Card", "Miami"),

 (103, "Maya Harmadez", "Credit Card", "Seattle"),

 (104, "Liam Donovan", "Netbanking", "Denver"),

 (105, "Sophia Nguyen", "Credit Card", "New Orleans"),

 (106, "Caleb Foster", "Debit Card", "Minneapolis"),

 (107, "Ava Patel", "Debit Card", "Phoenix"),

 (108, "Lucas Carter", "Netbaking", "Boston"),

 (109, "Isabella Martinez", "Netbaking", "Nashville"),

 (110, "Jaskson Brooks", "Credit Card", "Boston");

SELECT mode, COUNT(customer) FROM PAYMENT GROUP BY mode;

-- UPDATE

UPDATE PAYMENT SET mode = "NetBanking" WHERE mode = "Netbaking";

-- ADD COLUMN

ALTER TABLE payment ADD COLUMN code INT DEFAULT 2543;

-- MODIFY COLUMN

ALTER TABLE payment MODIFY COLUMN code VARCHAR(5);

-- if we add this data this will cause an error because it exceeds the limit

INSERT INTO payment (customer_id , customer, city , code) VALUES
(111, "James Barnes", "Seattle", 678574);
 
-- RENAME TABLE

ALTER TABLE payment RENAME TO payments ;

ALTER TABLE payments RENAME TO payment ;

-- CHANGE CLOUMN

ALTER TABLE payment CHANGE COLUMN code Pincode INT NULL;

-- DROP COLUMN

ALTER TABLE payment DROP COLUMN Pincode;

SELECT * FROM PAYMENT;

-- ----------------------------------------------------------------

-- Use of FOREIGN KEY --

USE college;

CREATE TABLE subjects(
 id INT PRIMARY KEY,
 subjects VARCHAR(10)
);

INSERT INTO subjects (id, subjects) VALUES

 (101, "English"),
 (102, "Maths"),
 (103, "Science"),
 (104, "Hindi"),
 (105, "Computer");
 
 -- UPDATE while cascading
 
 UPDATE subjects SET id = 111 WHERE id = 102 ;
 
 -- Deleting a row while cascading
 
 DELETE FROM  subjects WHERE id = 103;
 
SELECT * FROM subjects;
 
 -- CASCADING the tables --
 
 -- DROP TABLE teachers;
 
CREATE TABLE teachers(
 id INT PRIMARY KEY,
 name VARCHAR(20),
 dept_id INT,
 FOREIGN KEY (dept_id) REFERENCES subjects (id)
 ON UPDATE CASCADE
 ON DELETE CASCADE
);

INSERT INTO teachers (id, name, dept_id) VALUES

 (101, "Olivia Barrett", 102),
 
 (102, "Ethan Sinclair", 105),

 (103, "Maya Harmadez", 104),

 (104, "Liam Donovan", 101),

 (105, "Sophia Nguyen", 102),

 (106, "Caleb Foster", 103),

 (107, "Ava Patel", 105),

 (108, "Lucas Carter", 102);

SELECT * FROM teachers;

-- ---------------------------------------------------------------------------

-- USE OF TRUNCATE table --

USE xyz;

CREATE TABLE sample_Table(
 name VARCHAR(1),
 age INT 
);

INSERT INTO sample_Table (name, age) VALUES
  ("A", 45),("B", 65),("C", 76);
 
 SELECT * FROM sample_Table;
 
 -- TRUNCATE (deletes data from thw table)
 
 TRUNCATE TABLE sample_Table;
 
 -- --------------------------------------------------------------
 
 CREATE DATABASE HOGWARTS;
 
 USE HOGWARTS;
 
 CREATE TABLE Students (
 ID INT PRIMARY KEY,
 name VARCHAR(30),
 marks INT NOT NULL,
 grade VARCHAR(1)
 );
 
 INSERT INTO Students VALUES(101, "Neville Longbottom", 78, "C");
 
 INSERT INTO Students VALUES(102, "Draco Malfoy", 93, "A");
 
 INSERT INTO Students VALUES(103, "Harry Potter", 85, "B");
 
 INSERT INTO Students VALUES(104, "Hermoine Granger", 96, "A");
 
 INSERT INTO Students VALUES(105, "Ronald Weasley", 62, "D");
 
 INSERT INTO Students VALUES(106, "Luna Lovegood", 82, "B");
 
 SELECT * FROM Students;
 
 -- PRACTICE QUERIES
 
 -- CHANGE THE NAME 
 
 ALTER TABLE Students CHANGE COLUMN name full_name VARCHAR(30);
 
 -- disable the safe update
 
 SET SQL_SAFE_UPDATES = 0;
 
 -- DELETE all students scoring less than 80
 
 DELETE FROM Students WHERE marks < 80;
 
 -- DELETE grade column
 
 ALTER TABLE Students DROP COLUMN grade; 

 ------------------------------------------------------------------------------------------------

CREATE DATABASE IF NOT EXISTS SCHOOL;
 
USE SCHOOL;

CREATE TABLE student(
 student_id INT PRIMARY KEY,
 name VARCHAR(20)
);
 
INSERT INTO student (student_id, name) VALUES
 (101, "Peter Parker"),(102, "Miles Morales"),(103, "Pietro Maximoff");
 
SELECT * FROM student;
 
CREATE TABLE course(
 id INT PRIMARY KEY,
 course VARCHAR(10)
);
 
INSERT INTO course (id, course) VALUES
 (107, "English"),(102, "Maths"),(103, "Chemistry"),(110, "Hindi");
 
SELECT * FROM course;
 
-- JOINS IN SQL --

-- INNER JOIN

SELECT * FROM student INNER JOIN course ON student.student_id = course.id ;
 
-- Using AS (Alias Name for table)--

SELECT * FROM student AS s INNER JOIN course AS c ON s.student_id = c.id ; 

-- LEFT JOIN

SELECT * FROM student AS s LEFT JOIN course AS c ON s.student_id = c.id ; 

-- RIGHT JOIN

SELECT * FROM student AS s RIGHT JOIN course AS c ON s.student_id = c.id ; 

-- FULL JOIN using FEF / RIGHT / UNION

SELECT * FROM student AS s LEFT JOIN course AS c ON s.student_id = c.id  
UNION
SELECT * FROM student AS s RIGHT JOIN course AS c ON s.student_id = c.id ; 

-- LEFT EXCLUSIVE JOIN

SELECT * FROM student AS s LEFT JOIN course AS c ON s.student_id = c.id WHERE c.id IS NULL;

-- RIGHT EXCLUSIVE JOIN

SELECT * FROM student AS s RIGHT JOIN course AS c ON s.student_id = c.id WHERE s.student_id IS NULL ;

-- FULL EXCLUSIVE JOIN

SELECT * FROM student AS s LEFT JOIN course AS c ON s.student_id = c.id WHERE c.id IS NULL
UNION
SELECT * FROM student AS s RIGHT JOIN course AS c ON s.student_id = c.id WHERE s.student_id IS NULL ;

-- ---------------------------------------------------------------------------------------------------------------

-- SELF JOIN --

USE employee;

CREATE TABLE employee(
 id INT PRIMARY KEY,
 name VARCHAR(20),
 manager_id INT
); 

INSERT INTO employee(id, name, manager_id) VALUES
 (101, "steve" , 104),(102, "bruce" , 103),(103, "tony", NULL),(104, "clint" , 102);
 
SELECT * FROM employee;

-- SIMPLE JOIN / SELF JOIN --

SELECT * FROM employee AS A JOIN employee AS B ON A.id = B.manager_id;

-- SELF JOIN to print just the names of a and b table

SELECT a.name , b.name FROM employee AS A JOIN employee AS B ON A.id = B.manager_id;

-- SELF JOIN to print just the names and manager names of a and b table

SELECT a.name AS manager_name , b.name FROM employee AS A JOIN employee AS B ON A.id = B.manager_id;

-- to print the name before manager name

SELECT b.name ,a.name AS manager_name  FROM employee AS A JOIN employee AS B ON A.id = B.manager_id;

-- UNION  (gives unique values) --

SELECT * FROM employee 
UNION
SELECT * FROM employee;

-- to print all unique names

SELECT name FROM employee 
UNION
SELECT name FROM employee;

-- UNION ALL (includes duplicate values) 

SELECT * FROM employee 
UNION ALL
SELECT * FROM employee;

-- to print all names in both tables

SELECT name FROM employee 
UNION ALL
SELECT name FROM employee;

-- ----------------------------------------------------------------------------------------------------

USE school;

-- UNION (gives unique values)-- 

SELECT * FROM course 
UNION
SELECT * FROM student;

-- UNION ALL (includes duplicate values) 

SELECT * FROM course 
UNION ALL
SELECT * FROM student;

-- --------------------------------------------------------------------------

-- SUB QUERIES IN SQL --

-- to print the names of students who scored more than the average marks

 USE college;
 
 SELECT AVG(marks) FROM student;
 
 SELECT name, marks FROM student WHERE marks > 87.8000;
  
-- but the correct way to do this is using sub queries

SELECT name, marks FROM student WHERE marks > (SELECT AVG(marks) FROM student);

-- to print the names of all students with even roll no.

SELECT name, rollno FROM student WHERE rollno % 2 = 0;


-- sub query

SELECT name, rollno FROM student WHERE rollno IN (SELECT rollno FROM student WHERE rollno % 2 = 0);

-- WITH FROM

-- to print the max marks from the students of delhi

SELECT MAX(marks) FROM student WHERE city = "Delhi";

-- sub query with alias

SELECT MAX(marks) FROM (SELECT * FROM student WHERE city = "Delhi") AS temp;

-- for mumbai

SELECT MAX(marks) FROM (SELECT * FROM student WHERE city = "Mumbai") AS temp;

-- WITH SELECT

SELECT (SELECT MAX(marks) FROM student) , name FROM student;



