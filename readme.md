-- creat edatabase  
create database college;

-- comment given by -- 

--  usethe database 
Use college;

--  create a table 
create table student(
id INT primary key,
name varchar(50),
age INt not null
);

-- insert the data into the table 
Insert into student values(1,"vaibhav",22);
Insert into student values(2,"purva",19);

--  show the table  
select * from student;

drop tables student;

create table student(
rollno INT primary key,
name varchar(50)
);

-- show complete table 
select * from student;

-- insert the data in single row each 
Insert into student values(1,"vaibhav");
Insert into student values(2,"purva");

insert into student (rollno,name) values (3,"vaishnavi"), (4,"sakshi");

-- show table 
select * from student;
 
 -- quiz  
 create database xyz_comp;
 use xyz_comp;
 -- create a table with colm id, name , salary for employee 
 create table employee(
 id int primary key,
 name varchar(50) ,
 salary int default 25000
 );
 --drop TABLE employee;
 
 insert into employee (id, name, salary)values (1,"adam",25000),(2,"bob",30000),(3,"casey", 40000);
 select * from employee;
 
 DROP TABLE STUDENT;
 -- Create the table
CREATE TABLE STUDENT(
ROLLNO INT primary KEY,
NAME VARCHAR(50),
MARKS INT NOT NULL,
GRADE VARCHAR(1),
CITY VARCHAR(20)
);


-- -----------------------------------------------------------------
-- Insert data into the table
INSERT INTO student (rollno, name, marks, grade, city)
VALUES
    (101, "anil", 78, "C", "Pune"),
    (102, "bhumika", 93, "A", "Mumbai"),
    (103, "chetan", 85, "B", "Mumbai"),
    (104, "dhruv", 96, "A", "Delhi"),
    (105, "emanuel", 12, "F", "Delhi"),
    (106, "farah", 82, "B", "Delhi");
    
SELECT * FROM STUDENT; 
 
SELECT distinct city from student;

-- where cluase ;
-- student who has marks greater than 80
select* 
from student 
where marks >80;

select * from student 
where city="delhi" and marks>80;

-- |operators|
-- ----------
-- arithmetic operator --> +,-,*,/. modulo %
-- comparision operator --> =,!=,>, >=,<=
-- logical operator  --> AND ,OR ,NOT ,IN ,BETWEEN , ALL, LIKE , ANY 
-- BITWISE OPERATOR  --> & BITWISE AND , | BITWISE OR

-- AND - BOTH CONDITIONS ARE TRUE
SELECT* FROM STUDENT
WHERE MARKS>=82 AND CITY="MUMBAI";

-- OR - FALSE WHEN BOTH CONDITIONS ARE FALSE ; OTHERWISE TRUE ,EITHER ONE IS TRUE , FALSE CONDITION 
SELECT * FROM STUDENT
where MARKS>=82 OR CITY="MUMBAI";

-- BETWEEN - SELECTS THE INCLUSIVE RANGE
 SELECT * FROM STUDENT 
 WHERE MARKS between 80 AND 90;
 
 -- IN - MATCHES ANY VALUE IN THE LIST
 SELECT * FROM student 
 WHERE CITY IN ("DELHI","MUMBAI");
 
 -- NOT- TO NEGATE THE GIVEN CONDITION 
 SELECT * FROM STUDENT WHERE CITY NOT IN("DELHI","MUMBAI");
 
 -- LIMIT CLUASE SETS AN UPPER LIMUT ON NUMBER OF TUPLES ROW TO BE RETURN alter
 SELECT * FROM 
 STUDENT LIMIT 3;
 
 
 -- ORDER BY CLUASE 
 -- ASC OR DESC 
 SELECT * FROM STUDENT
 ORDER BY MARKS ASC;
 
 -- PRINT 3 TOPPER 
 SELECT *FROM STUDENT 
 ORDER BY MARKS DESC LIMIT 3;
 
 -- agggregate functions --> perform a calculation on set of values and return a single value 
 -- count() , max() , min() , sum() , avg()
 
 -- find avg maeks
 select avg(marks)
 from student;
 -- count()
 select count(marks)
 from student;
 
 -- maximum marks 
 select max(marks)
 from student;
 -- minimum marks
 select min(marks)
 from student;
 
-- sum()
select sum(marks)
from student;

-- -------------------
 -- group by clause --> groups row that have same value into summary rows
 -- it collects data from multiple records and group the result by one or more colm
 --  generally we use group by with some aggregate functions 
 
 -- count the number of student in each city 
 select city,count(name)
 from student
 group by city ;
 
 -- write a query to find avg marks in each city in asc order 
 select city,avg(marks)
 from student
 group by city
 order by avg(marks) ASC ;
 
 -- having cluase
 --  similar to where cluase i.e applies some condition on row 
 -- used when we want to apply any conditions after grouping 
 
 -- que count the number of student in each city where max marks cross 90 
 select city, count(name)
 from student
 group by city
 having max(marks)>90;
 
-- table related queries 
-- update 
set sql_safe_updates=0;

update student
set grade="O"
where grade ="A"; 

select * from student;
-- delete operation 
delete from student
where marks < 33;

select * from student;

create table DEPARTMENT(
id int primary key,
name varchar(50)
);
CREATE TABLE TEACHER(
ID INT PRIMARY KEY,
NAME VARCHAR(50),
DEPT_ID INT,
FOREIGN KEY (DEPT_ID)references DEPARTMENT(ID)
on update cascade
on delete cascade
);
drop table teacher;

INSERT INTO DEPARTMENT (ID, NAME)
VALUES (101, 'Computer Science'), (102, 'Mathematics');

INSERT INTO TEACHER (ID, NAME, DEPT_ID)
VALUES (101, 'Adam', 101), (102, 'Eve', 102);

select * from teacher;

-- table related queries 
-- alter -- to change the schema 
-- add column
-- drop column 
-- rename table 

Alter table teacher
add column age int not null default 19;

-- modify 
alter table teacher
modify column age varchar(2);



INSERT INTO TEACHER (ID, NAME, DEPT_ID,age)
VALUES (103, 'Adam11', 103,44), (104, 'Eve11', 104,55);


-- joins in sql 
drop table student;

-- ---------
-- Create the STUDENT table
CREATE TABLE STUDENT (
    STUDENT_ID INT PRIMARY KEY,
    NAME VARCHAR(50)
);

-- Insert data into the STUDENT table
INSERT INTO STUDENT (STUDENT_ID, NAME)
VALUES
    (101, 'ADAM'),
    (102, 'BOB'),
    (103, 'CASEY');

-- Create the COURSE table
CREATE TABLE COURSE (
    STUDENT_ID INT,
    COURSE VARCHAR(50),
    PRIMARY KEY (STUDENT_ID),
    FOREIGN KEY (STUDENT_ID) REFERENCES STUDENT(STUDENT_ID)
);

-- Insert data into the COURSE table
-- Ensure that STUDENT_ID exists in the STUDENT table
INSERT INTO COURSE (STUDENT_ID, COURSE)
VALUES 
    (102, 'english'),
    (103, 'science'); -- Removed 105 and 107 because they don't exist in the STUDENT table


    
INSERT INTO STUDENT (STUDENT_ID, NAME)
VALUES
    (105, 'DAVID'),
    (107, 'EVA');

INSERT INTO COURSE (STUDENT_ID, COURSE)
VALUES 
    (105, 'math'),
    (107, 'computer science');
    
    -- INNER JOIN 
 SELECT *
FROM STUDENT
INNER JOIN COURSE
ON STUDENT.STUDENT_ID = COURSE.STUDENT_ID;
   -- LEFT JOIN 
    SELECT *
FROM STUDENT
LEFT JOIN COURSE
ON STUDENT.STUDENT_ID = COURSE.STUDENT_ID;

-- RIGHT JOIN 
 SELECT *
FROM STUDENT
RIGHT JOIN COURSE
ON STUDENT.STUDENT_ID = COURSE.STUDENT_ID;

-- full join 
SELECT *
FROM STUDENT
LEFT JOIN COURSE
ON STUDENT.STUDENT_ID = COURSE.STUDENT_ID;
union
SELECT *
FROM STUDENT
RIGHT JOIN COURSE
ON STUDENT.STUDENT_ID = COURSE.STUDENT_ID;
    
-- left exclusive join and right exlusive join 
select * from student as a
left join course as b 
on a.student_id=b.student_id;
where b.student_id is null;


-- Rows from student that don't match course
SELECT *
FROM student AS a
LEFT JOIN course AS b
ON a.student_id = b.student_id
WHERE b.student_id IS NULL
UNION
-- Rows from course that don't match student
SELECT *
FROM student AS a
RIGHT JOIN course AS b
ON a.student_id = b.student_id
WHERE a.student_id IS NULL;

-- self join -> it is regular join , but table is joined with itself 

create table employee(
id int primary key ,
name varchar(50),
manager_id int
);
insert into employee(id,name,manager_id)
values
(101,"adam",103),
(102,"bob",104),
(103,"casey",null),
(104,"donald",103);

select * from employee;

-- self join 
select a.name as manager_name,b.name
from employee as a
join employee as b
on a.id=b.manager_id; 

--  union -- join both table make union and just give unique tuple 
-- union all -> it give complete data including duplicate 
select name from employee
union all
select name from employee;

select name from employee
union 
select name from employee;

-- sub- queries 
create table marks(
rollno int primary key,
name varchar(50) ,
marks int 
);
-- Create the marks table with an additional city column
CREATE TABLE marks (
    rollno INT PRIMARY KEY,
    name VARCHAR(50),
    marks INT,
    city VARCHAR(50)
);

-- Insert data into the marks table
INSERT INTO marks (rollno, name, marks, city)
VALUES 
    (101, 'anil', 78, 'Pune'),
    (102, 'bhumika', 93, 'Mumbai'),
    (103, 'chetan', 85, 'Mumbai'),
    (104, 'dhruv', 96, 'Delhi'),
    (105, 'emanuel', 92, 'Delhi'),
    (106, 'vaibhav', 82, 'Delhi');

 
--  Find the Name of the Student with the Highest Marks:
select name
from marks
where marks = (
select max(marks) from marks
);

-- Find Students Who Scored Above the Average Marks:
select name,marks
from marks
where marks>(select avg(marks) from marks);

-- Find the Roll Number of Students with Marks Less Than 90:
select rollno,name
from marks
where marks<90;
-- Check If a Specific Student Exists in the Table:
select * 
from marks
where name="vaibhav" and rollno in(select rollno from marks);

-- Find the Second Highest Marks Using a Subquery:
select max(marks) 
from marks
where marks < (select max(marks) from marks);

-- find the names of student with even roll number 
select name,rollno
from marks
where rollno %2=0;

-- from k andar wali query 
-- find max marks from the student of delhi 
-- step 1 find the student of delhi 
-- step 2 find their max marks using the sublist step 1 

select max(marks)
from (
select *
from marks
where city="delhi" ) as temp;

-- or 
select max(marks)
from marks
where city="delhi";

-- create a view 
create view view1 As
select rollno,name,marks from marks;

select * from view1;



 

