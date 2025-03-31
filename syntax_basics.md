```sql
-- Creating a sample database & table
CREATE DATABASE LearningSQL;
USE LearningSQL;

CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    department VARCHAR(50)
);

INSERT INTO employees (id, name, age, department) VALUES (1, 'Alice', 28, 'HR');

```
![image](https://github.com/user-attachments/assets/87c390d8-28ab-4850-ace3-49636d4ccb9a)

```sql
SELECT * FROM employees WHERE age > 25;

```
![image](https://github.com/user-attachments/assets/505a921b-86d4-4b36-83c4-4262aaa98b32)

```sql
-- Create table departments
CREATE TABLE departments (
    id INT PRIMARY KEY,
    department_name VARCHAR(50)
);

-- Insert records into Departments table
INSERT INTO departments (id, department_name) VALUES
(1, 'HR'),
(2, 'IT'),
(3, 'Finance'),
(4, 'Marketing');
```
![image](https://github.com/user-attachments/assets/8329c829-bdcb-4277-b30c-937a2a847ebb)

```sql
-- Create Employees table
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);

-- Insert 10 records into Employees table
INSERT INTO employees (id, name, age, department_id) VALUES
(1, 'Alice', 28, 1),
(2, 'Bob', 34, 2),
(3, 'Charlie', 29, 3),
(4, 'David', 41, 4),
(5, 'Eve', 37, 2),
(6, 'Frank', 26, 1),
(7, 'Grace', 32, 3),
(8, 'Hank', 45, NULL), -- No department assigned
(9, 'Ivy', 30, 4),
(10, 'Jack', 27, NULL); -- No department assigned
```
![image](https://github.com/user-attachments/assets/878e7531-d9e9-4cfd-9f8c-830c78652e1a)

Output:
![image](https://github.com/user-attachments/assets/2be3c2e7-a278-47da-9d6e-9cce21238f9d)
