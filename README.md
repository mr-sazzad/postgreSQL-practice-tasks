1️⃣ Task 1: SELECT and WHERE Clause Create a table named "employees" with columns (emp_id, emp_name, department, salary) and insert the following data:
```sql

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    department VARCHAR(50),
    salary DECIMAL(10, 2)
);

INSERT INTO employees (emp_id, emp_name, department, salary)
VALUES
    (1, 'John Doe', 'HR', 50000.00),
    (2, 'Jane Smith', 'IT', 60000.00),
    (3, 'Michael Johnson', 'Finance', 55000.00),
    (4, 'Emily Brown', 'HR', 52000.00);
```

Write an SQL query to retrieve the names and salaries of employees who work in the "HR" department.

Expected Result:
| emp_name | salary |
|----------------|-----------|
| John Doe | 50000.00 |
| Emily Brown | 52000.00 |

```sql
-- ANSWARE 1

SELECT emp_name, salary FROM employees WHERE department = 'HR';
```

2️⃣ Task 2: Aggregation and HAVING Clause
Create a table named "orders" with columns (order_id, customer_id, total_amount) and insert the following data:

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    total_amount DECIMAL(10, 2)
);

INSERT INTO orders (order_id, customer_id, total_amount)
VALUES
    (101, 1, 200.00),
    (102, 2, 300.00),
    (103, 1, 150.00),
    (104, 3, 400.00),
    (105, 2, 250.00);
```

Write an SQL query to find the customer IDs and the average total amount of their orders. Display only those customers whose average total amount is greater than or equal to 250.

Expected Result:
| customer_id | average_total_amount |
|----------------|----------------------|
| 2 | 275.00 |

```sql
-- ANSWARE 2

SELECT customer_id, total_amount FROM orders WHERE total_amount >= 250;
```


3️⃣ Task 3: JOIN and GROUP BY
Create two tables named "students" and "courses" with columns as follows:

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    age INT,
    gender VARCHAR(10)
);

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(50),
    credits INT
);

INSERT INTO students (student_id, student_name, age, gender)
VALUES
    (1, 'Alice', 22, 'Female'),
    (2, 'Bob', 21, 'Male'),
    (3, 'Charlie', 23, 'Male');

INSERT INTO courses (course_id, course_name, credits)
VALUES
    (101, 'Mathematics', 3),
    (102, 'History', 4),
    (103, 'Physics', 3);

-- Enrollment table with student-course relationships
CREATE TABLE enrollment (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT
);

INSERT INTO enrollment (enrollment_id, student_id, course_id)
VALUES
    (1, 1, 101),
    (2, 1, 102),
    (3, 2, 103),
    (4, 3, 101);
```

Write an SQL query to retrieve the student name, course name, and credits for all enrolled courses.

Expected Result:
| student_name | course_name | credits |
|----------------|----------------|---------|
| Alice | Mathematics | 3 |
| Alice | History | 4 |
| Bob | Physics | 3 |
| Charlie | Mathematics | 3 |
