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
-- ANSWER 1 ✅

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
-- ANSWER 2 ✅

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

```sql
-- ANSWER 3 ✅

SELECT s.student_name, c.course_name, c.credits
FROM students s
JOIN enrollment e ON s.student_id = e.student_id
JOIN courses c ON e.course_id = c.course_id;
```

4️⃣ Task 4: Multiple Joins and Aggregation
Create three tables named "employees," "departments," and "salaries" with columns as follows:

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    department_id INT
);

CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(50)
);

CREATE TABLE salaries (
    emp_id INT,
    salary DECIMAL(10, 2)
);

INSERT INTO employees (emp_id, emp_name, department_id)
VALUES
    (1, 'John Doe', 1),
    (2, 'Jane Smith', 2),
    (3, 'Michael Johnson', 1),
    (4, 'Emily Brown', 3);

INSERT INTO departments (department_id, department_name)
VALUES
    (1, 'HR'),
    (2, 'IT'),
    (3, 'Finance');

INSERT INTO salaries (emp_id, salary)
VALUES
    (1, 50000.00),
    (2, 60000.00),
    (3, 55000.00),
    (4, 52000.00);
```

Write an SQL query to retrieve the department name and the average salary of employees working in each department. Sort the results by the average salary in descending order.

Expected Result:
| department_name | average_salary |
|-------------------|----------------|
| IT | 60000.00 |
| HR | 52500.00 |
| Finance | 52000.00 |

```sql
-- ANSWER - 4 ✅

    SELECT department_name, AVG(salary) AS avg_salary 
    FROM employees e 
    JOIN salaries s ON e.emp_id = s.emp_id 
    JOIN departments d ON e.department_id = d.department_id 
    GROUP BY d.department_name -- complex part
    ORDER BY avg_salary DESC;
```

5️⃣ Task 5: Aggregation and Grouping
Create a table named "orders" with columns (order_id, customer_id, order_date, total_amount) and insert the following data:

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10, 2)
);

INSERT INTO orders (order_id, customer_id, order_date, total_amount)
VALUES
    (101, 1, '2023-01-05', 200.00),
    (102, 2, '2023-01-06', 300.00),
    (103, 1, '2023-02-10', 150.00),
    (104, 3, '2023-02-15', 400.00),
    (105, 2, '2023-03-20', 250.00);
```

Write an SQL query to find the total sales amount for each month, along with the number of orders in that month.

Expected Result:
| Month | Total_Sales | Num_Orders |
|----------|-------------|------------|
| January | 550.00 | 2 |
| February | 550.00 | 2 |
| March | 250.00 | 1 |


```sql

--answer - 5 ✅

SELECT 
    TO_CHAR(order_date, 'Month') AS Month,
    SUM(total_amount) AS Total_Sales,
    COUNT(*) AS Num_Orders
FROM orders
GROUP BY Month
ORDER BY Month DESC;


SELECT 
    CASE EXTRACT(MONTH FROM order_date)
        WHEN 1 THEN 'January'
        WHEN 2 THEN 'February'
        WHEN 3 THEN 'March'
        WHEN 4 THEN 'April'
        WHEN 5 THEN 'May'
        WHEN 6 THEN 'June'
        WHEN 7 THEN 'July'
        WHEN 8 THEN 'August'
        WHEN 9 THEN 'September'
        WHEN 10 THEN 'October'
        WHEN 11 THEN 'November'
        WHEN 12 THEN 'December'
    END AS Month,
    SUM(total_amount) AS Total_Sales,
    COUNT(*) AS Num_Orders
FROM orders
GROUP BY EXTRACT(MONTH FROM order_date)
ORDER BY EXTRACT(MONTH FROM order_date);

```
