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

SHOW DATABASES;

SHOW TABLES;

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

SELECT * FROM student;

SELECT name, marks, grade FROM student;

-- DISTINCT KEYWORD

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

-- GROUP BY / COUNT

SELECT city, COUNT(name) FROM student GROUP BY city; 





