
# SQL Concepts and Queries

## Database and Table Creation

1. **Creating a Database:**
   ```sql
   CREATE DATABASE college;
   ```

2. **Using the Database:**
   ```sql
   USE college;
   ```

3. **Creating a Table:**
   ```sql
   CREATE TABLE student(
       id INT PRIMARY KEY,
       name VARCHAR(50),
       age INT NOT NULL
   );
   ```

4. **Inserting Data into a Table:**
   ```sql
   INSERT INTO student VALUES(1, 'Vaibhav', 22);
   INSERT INTO student VALUES(2, 'Purva', 19);
   ```

5. **Showing the Table Data:**
   ```sql
   SELECT * FROM student;
   ```

6. **Dropping the Table:**
   ```sql
   DROP TABLE student;
   ```

## Altering Tables

1. **Modifying a Table Schema:**
   ```sql
   ALTER TABLE teacher
   ADD COLUMN age INT NOT NULL DEFAULT 19;
   ```

2. **Renaming a Table:**
   ```sql
   ALTER TABLE student RENAME TO new_student;
   ```

## Data Manipulation

1. **Updating Data:**
   ```sql
   SET sql_safe_updates = 0;

   UPDATE student
   SET grade = 'O'
   WHERE grade = 'A';
   ```

2. **Deleting Data:**
   ```sql
   DELETE FROM student WHERE marks < 33;
   ```

3. **Inserting Data in Single Rows:**
   ```sql
   INSERT INTO student (rollno, name) VALUES (1, 'Vaibhav');
   INSERT INTO student (rollno, name) VALUES (2, 'Purva');
   ```

4. **Inserting Multiple Rows:**
   ```sql
   INSERT INTO student (rollno, name) VALUES (3, 'Vaishnavi'), (4, 'Sakshi');
   ```

## Filtering and Querying Data

1. **Using WHERE Clause:**
   ```sql
   SELECT * FROM student WHERE marks > 80;
   ```

2. **Using Logical Operators (AND, OR, NOT, IN, BETWEEN):**
   ```sql
   -- AND - Both conditions are TRUE
   SELECT * FROM student WHERE marks >= 82 AND city = 'Mumbai';

   -- OR - At least one condition is TRUE
   SELECT * FROM student WHERE marks >= 82 OR city = 'Mumbai';

   -- BETWEEN - Inclusive range
   SELECT * FROM student WHERE marks BETWEEN 80 AND 90;

   -- IN - Matches any value in the list
   SELECT * FROM student WHERE city IN ('Delhi', 'Mumbai');

   -- NOT - Negate the condition
   SELECT * FROM student WHERE city NOT IN ('Delhi', 'Mumbai');
   ```

3. **Using LIMIT Clause:**
   ```sql
   SELECT * FROM student LIMIT 3;
   ```

4. **Using ORDER BY Clause:**
   ```sql
   -- Ascending order
   SELECT * FROM student ORDER BY marks ASC;

   -- Top 3 students by marks
   SELECT * FROM student ORDER BY marks DESC LIMIT 3;
   ```

## Aggregate Functions

1. **Finding Average Marks:**
   ```sql
   SELECT AVG(marks) FROM student;
   ```

2. **Counting Records:**
   ```sql
   SELECT COUNT(marks) FROM student;
   ```

3. **Finding Maximum and Minimum Marks:**
   ```sql
   SELECT MAX(marks) FROM student;
   SELECT MIN(marks) FROM student;
   ```

4. **Summing Marks:**
   ```sql
   SELECT SUM(marks) FROM student;
   ```

## Grouping Data

1. **Using GROUP BY Clause:**
   ```sql
   -- Count number of students in each city
   SELECT city, COUNT(name) FROM student GROUP BY city;

   -- Average marks per city in ascending order
   SELECT city, AVG(marks) FROM student GROUP BY city ORDER BY AVG(marks) ASC;
   ```

2. **Using HAVING Clause:**
   ```sql
   -- Count number of students in each city where max marks are greater than 90
   SELECT city, COUNT(name)
   FROM student
   GROUP BY city
   HAVING MAX(marks) > 90;
   ```

## Joins

1. **INNER JOIN:**
   ```sql
   SELECT *
   FROM student
   INNER JOIN course ON student.student_id = course.student_id;
   ```

2. **LEFT JOIN:**
   ```sql
   SELECT *
   FROM student
   LEFT JOIN course ON student.student_id = course.student_id;
   ```

3. **RIGHT JOIN:**
   ```sql
   SELECT *
   FROM student
   RIGHT JOIN course ON student.student_id = course.student_id;
   ```

4. **FULL OUTER JOIN:**
   ```sql
   SELECT *
   FROM student
   LEFT JOIN course ON student.student_id = course.student_id
   UNION
   SELECT *
   FROM student
   RIGHT JOIN course ON student.student_id = course.student_id;
   ```

5. **Self Join:**
   ```sql
   SELECT a.name AS manager_name, b.name
   FROM employee AS a
   JOIN employee AS b ON a.id = b.manager_id;
   ```

## Subqueries

1. **Find Student with Highest Marks:**
   ```sql
   SELECT name
   FROM marks
   WHERE marks = (SELECT MAX(marks) FROM marks);
   ```

2. **Find Students Who Scored Above Average Marks:**
   ```sql
   SELECT name, marks
   FROM marks
   WHERE marks > (SELECT AVG(marks) FROM marks);
   ```

3. **Find Roll Numbers of Students with Marks Less Than 90:**
   ```sql
   SELECT rollno, name
   FROM marks
   WHERE marks < 90;
   ```

4. **Find the Second Highest Marks:**
   ```sql
   SELECT MAX(marks)
   FROM marks
   WHERE marks < (SELECT MAX(marks) FROM marks);
   ```

5. **Subquery within the Main Query:**
   ```sql
   SELECT MAX(marks)
   FROM marks
   WHERE city = 'Delhi';
   ```

## Creating Views

1. **Creating a View:**
   ```sql
   CREATE VIEW view1 AS
   SELECT rollno, name, marks
   FROM marks;
   ```

2. **Selecting from a View:**
   ```sql
   SELECT * FROM view1;
   ```

---

### Key Concepts

1. **Primary Key:** Uniquely identifies each row in a table.
2. **Foreign Key:** Establishes a relationship between two tables.
3. **Aggregate Functions:** Operations like `COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()` that work on a set of rows.
4. **Normalization:** Organizing data to reduce redundancy.
5. **Joins:** Combining data from multiple tables based on related columns (INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN).
6. **Subqueries:** A query inside another query, typically used for comparison or data selection.

---

### Download Link

To download this as a file, you can save the content into a `.txt` or `.md` file.
