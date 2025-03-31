
SQL Security, Backup & Restoration:

Now that we have our employees and departments tables with stored procedures, let's explore security, backup, and restoration concepts.

1.	User Privileges (Restricting Access):
Instead of giving full access to every user, restrict privileges using GRANT statements.

```sql
CREATE USER 'readonly_user'@'localhost' IDENTIFIED BY 'securepassword';

GRANT SELECT ON company.* TO 'readonly_user'@'localhost';
```

![image](https://github.com/user-attachments/assets/71ee3dce-809b-4324-b2e1-1c9303844d60)


This user can only run SELECT queries on the company database (assuming our tables are in company). The user cannot modify or delete data.

2. User with only insert access:
```sql
CREATE USER 'data_entry_user'@'localhost' IDENTIFIED BY 'password123';
GRANT INSERT ON learningschema.employees TO 'data_entry_user'@'localhost';
FLUSH PRIVILEGES;
```

![image](https://github.com/user-attachments/assets/5a82df3b-b22f-4b4f-8a80-f1914a52bced)

This user can only add new employees but cannot delete or update records.

3.	Revoking privileges:

```sql
REVOKE INPRIMARYSERT ON learningschema.employees FROM 'data_entry_user'@'localhost';
```
![image](https://github.com/user-attachments/assets/e46d8a61-b152-44e6-bd9a-088b02ddc002)

Backup strategies:
Full Database Backup (Using mysqldump):

``` bash
mysqldump -u root -p company > company_backup.sql
```

Table-Specific Backup: Take only employee table
``` bash
mysqldump -u root -p company employees > employees_backup.sql
```
Data Restoration:
Restoring the Entire Database
If the database is lost or corrupted, restore it using:
```bash
mysql -u root -p company < company_backup.sql
```
Restoring a Single Table:
```bash
mysql -u root -p company < employees_backup.sql
```
Prevention against SQL injection:
```sql
PREPARE stmt FROM 'SELECT * FROM employees WHERE name = ?';
SET @name = 'John Doe';
EXECUTE stmt USING @name;
```

![image](https://github.com/user-attachments/assets/d1eef931-9dae-43ce-864f-714fe4fdf9b1)
This ensures user input is properly escaped, preventing SQL injection.
```sql
GRANT SELECT, INSERT ON learningschema.* TO 'secure_user'@'192.168.1.100';

```
Restrict Users to Specific IP Addresses:

![image](https://github.com/user-attachments/assets/e748eeee-9d7e-40df-9d6c-98f05d999517)

Showing the privileges of current user:
```sql
SHOW GRANTS FOR CURRENT_USER()
```
![image](https://github.com/user-attachments/assets/b2b30d09-71c7-4c91-b600-e216f9224353)


