
# SQL Commands and Queries

This README provides a collection of SQL commands and queries categorized by their use cases, including table creation, data manipulation, joins, subqueries, and more.

---

## Database and Table Operations

### Create Database and Use It
```sql
CREATE DATABASE college;
USE college;
```

### Create Table `student`
```sql
CREATE TABLE student(
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT NOT NULL
);
```

### Insert Data into `student`
```sql
INSERT INTO student VALUES (1, "vaibhav", 22);
INSERT INTO student VALUES (2, "purva", 19);
```

### Drop Table
```sql
DROP TABLE student;
```

---

## Advanced SQL Queries

### Create and Insert Data into `marks` Table
```sql
CREATE TABLE marks (
    rollno INT PRIMARY KEY,
    name VARCHAR(50),
    marks INT,
    city VARCHAR(50)
);

INSERT INTO marks (rollno, name, marks, city)
VALUES 
    (101, 'anil', 78, 'Pune'),
    (102, 'bhumika', 93, 'Mumbai'),
    (103, 'chetan', 85, 'Mumbai'),
    (104, 'dhruv', 96, 'Delhi'),
    (105, 'emanuel', 92, 'Delhi'),
    (106, 'vaibhav', 82, 'Delhi');
```

### Subqueries
- **Find the Name of the Student with the Highest Marks:**
```sql
SELECT name
FROM marks
WHERE marks = (
    SELECT MAX(marks) FROM marks
);
```

- **Find Students Who Scored Above the Average Marks:**
```sql
SELECT name, marks
FROM marks
WHERE marks > (SELECT AVG(marks) FROM marks);
```

### Self Join
```sql
CREATE TABLE employee(
    id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT
);

INSERT INTO employee(id, name, manager_id)
VALUES
    (101, "adam", 103),
    (102, "bob", 104),
    (103, "casey", NULL),
    (104, "donald", 103);

SELECT a.name AS manager_name, b.name
FROM employee AS a
JOIN employee AS b
ON a.id = b.manager_id;
```

---

## Join Operations

### Inner Join
```sql
SELECT *
FROM student
INNER JOIN course
ON student.student_id = course.student_id;
```

### Full Outer Join
```sql
SELECT *
FROM student
LEFT JOIN course
ON student.student_id = course.student_id
UNION
SELECT *
FROM student
RIGHT JOIN course
ON student.student_id = course.student_id;
```

---

## Aggregate Functions and Group By

### Average Marks in Each City (Ascending Order)
```sql
SELECT city, AVG(marks)
FROM student
GROUP BY city
ORDER BY AVG(marks) ASC;
```

### Count Students in Each City Where Max Marks Cross 90
```sql
SELECT city, COUNT(name)
FROM student
GROUP BY city
HAVING MAX(marks) > 90;
```

---

## View Creation
```sql
CREATE VIEW view1 AS
SELECT rollno, name, marks FROM marks;

SELECT * FROM view1;
```

---

## How to Use
- Run the queries in your SQL environment.
- Use appropriate database management tools like MySQL Workbench, pgAdmin, or any SQL CLI.
