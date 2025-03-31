## Navigate to other pages 
 [SQL Basics & Clauses](01_Syntax_Basics/syntax_basics.md)  
 [CRUD Operations, Joins & Aggregations](02_CRUD_Joins_Aggregations/crud_joins.md)  
 [Indexes & Constraints](03_Indexes_Constraints/indexes_constraints.md)  
 [Query Optimization & Indexes](04_Query_Optimization/query_optimization.md)  
 [SQL Security & Backup](06_Security_Backup/security_backup.md)  

Stored procedures:

A stored procedure is a reusable SQL script that executes a task. Here, we'll create one to insert new employees without writing INSERT manually each time.
```sql
CREATE PROCEDURE AddEmployee(
    IN emp_id INT,
    IN emp_name VARCHAR(100),
    IN emp_age INT,
    IN dept_id INT
)
BEGIN
    INSERT INTO employees (id, name, age, department_id) 
    VALUES (emp_id, emp_name, emp_age, dept_id);
END $$

DELIMITER ;

```
![image](https://github.com/user-attachments/assets/ee7ee7ea-9ae9-4c9e-9560-a7e819c9e7a2)

Calling a procedure:
```sql
CALL AddEmployee(101, 'John Doe', 29, 1);
CALL AddEmployee(102, 'Jane Smith', 34, 2);

```
![image](https://github.com/user-attachments/assets/1bd9ab93-7fba-452d-9dd0-b7c672b9c28e)

Dropping a procedure:
```sql
DROP PROCEDURE IF EXISTS AddEmployee;
```

![image](https://github.com/user-attachments/assets/8d729e1b-65ae-4959-a235-a1690855cc1c)

Functions:
A function returns a value. We'll create one to count employees in a department.
```sql
-- function
DELIMITER $$

CREATE FUNCTION CountEmployees(dept_id INT) 
RETURNS INT 
DETERMINISTIC
BEGIN
    DECLARE emp_count INT;
    SELECT COUNT(*) INTO emp_count FROM employees WHERE department_id = dept_id;
    RETURN emp_count;
END $$

DELIMITER ;
```
![image](https://github.com/user-attachments/assets/95d08366-cdb2-4eab-9a76-743191c469c7)

Calling a function:
```sql
SELECT CountEmployees(1);  -- Returns number of employees in department 1
SELECT CountEmployees(2);  -- Returns number of employees in department 2
```
![image](https://github.com/user-attachments/assets/49c04664-7581-4fce-8ae9-56ec80130649)

Stored Procedures simplify inserting data 
Functions make querying faster & reusable 

