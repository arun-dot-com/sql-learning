
```sql
DELETE FROM employees where id=1;
SELECT * FROM employees;
```
![image](https://github.com/user-attachments/assets/fa155a64-f3d4-4a18-8b03-84fe8bf3c282)

```sql
DROP table employees;
```
![image](https://github.com/user-attachments/assets/1c5ffd94-47a2-4e75-8d8b-36c0f2b918f6)


Inner Join:

```sql
-- INNER JOIN: Matches records with a common department_id
SELECT e.name, d.department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.id;
```

![image](https://github.com/user-attachments/assets/da853168-3e9a-42b6-8cd4-dbaf9bd417c6)

Left Join:

```sql
-- LEFT JOIN: Includes all employees, even if they don't belong to a department
SELECT e.name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.id;

```
![image](https://github.com/user-attachments/assets/722fd5e8-a7d0-4180-b45b-39c9bed59052)

Right Join:
```sql
-- RIGHT JOIN: Includes all departments, even if no employees belong to them
SELECT e.name, d.department_name
FROM employees e
RIGHT JOIN departments d ON e.department_id = d.id;
```
![image](https://github.com/user-attachments/assets/489731d5-02b1-4d4f-bd90-91e862c514ff)

Full Outer Join:

```sql
-- FULL OUTER JOIN: Includes all employees and departments (Not supported in MySQL directly, use UNION)
SELECT e.name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.id
UNION
SELECT e.name, d.department_name
FROM employees e
RIGHT JOIN departments d ON e.department_id = d.id;
```
![image](https://github.com/user-attachments/assets/42c55cec-db36-4c1a-b7ec-243b96d5931a)

Cross Join:
```sql
-- CROSS JOIN: Matches each employee with every department
SELECT e.name, d.department_name
FROM employees e
CROSS JOIN departments d;
```

![image](https://github.com/user-attachments/assets/c23969d9-e74a-4979-9d81-e6dd16780cc1)



