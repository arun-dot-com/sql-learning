
Indexes speed up search and JOIN operations.
Constraints enforce data integrity, preventing bad data entry.

Constraints on Employees table:

```sql
-- Modify Employees table to add constraints
ALTER TABLE employees 
ADD CONSTRAINT chk_age CHECK (age > 18); -- Age must be greater than 18

ALTER TABLE employees 
ADD CONSTRAINT uq_name UNIQUE (name); -- Employee names must be unique
```

![image](https://github.com/user-attachments/assets/faf52794-0b1d-4d2e-b136-5bd809bfb0fd)

Constraint on Departments table:

```sql
-- Modify Departments table to add constraints
ALTER TABLE departments 
ADD CONSTRAINT uq_department_name UNIQUE (department_name); -- No duplicate department names
```
![image](https://github.com/user-attachments/assets/5c3c4ad1-4638-4c26-b642-b9b8e0f9b6dc)

Adding indexes:

```sql
-- Create an index on the department_id column for faster joins
CREATE INDEX idx_department_id ON employees(department_id);

-- Create an index on the employee name for fast searches
CREATE INDEX idx_employee_name ON employees(name);

-- Create an index on the department name for quick lookups
CREATE INDEX idx_department_name ON departments(department_name);
```
![image](https://github.com/user-attachments/assets/d6a05130-a20f-412d-a55a-f21fa31a627a)

Verification of usage of indexes:
```sql
EXPLAIN ANALYZE 
SELECT e.name, d.department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.id;
```

![image](https://github.com/user-attachments/assets/ee055028-e912-4778-bbe3-92ae81b0dcae)

Testing the implementation of constraints: It fails correctly
```sql
-- This should fail due to CHECK constraint (age < 18)
INSERT INTO employees (id, name, age, department_id) VALUES (11, 'Tom', 16, 2);

-- This should fail due to UNIQUE constraint on employee name
INSERT INTO employees (id, name, age, department_id) VALUES (12, 'Alice', 30, 3);
```

![image](https://github.com/user-attachments/assets/9b734054-55b4-4d86-8903-530c8eda4142)


