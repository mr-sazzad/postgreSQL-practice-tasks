Task 1: SELECT and WHERE Clause Create a table named "employees" with columns (emp_id, emp_name, department, salary) and insert the following data:
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
