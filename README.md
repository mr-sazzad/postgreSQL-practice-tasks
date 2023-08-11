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
