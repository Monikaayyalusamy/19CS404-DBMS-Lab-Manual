# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
---
Question 1
For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name type

product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

---
sql
```
UPDATE Products 
SET sell_price = CAST(cost_price * 1.35 AS INT)
WHERE ((sell_price - cost_price) / sell_price) * 100 < 30;
```

**Output:**

<img width="1246" height="277" alt="image" src="https://github.com/user-attachments/assets/f95ed335-df41-420e-ae64-c9ec7fc68867" />


**Question 2**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id
---
sql
```
UPDATE Employees
SET salary = salary + 500,
email = 'updated'
WHERE job_id = 'SA_REP'
AND commission_pct > 0.15;
```

**Output:**

<img width="1310" height="382" alt="image" src="https://github.com/user-attachments/assets/9e3ce301-1bae-4c3b-94a2-476fbd76bafb" />


**Question 3**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table

name type

supplier_id INT supplier_name VARCHAR(100) contact_person VARCHAR(100) phone_number VARCHAR(20) email VARCHAR(100) address VARCHAR(250)
---
```sql
UPDATE Suppliers 
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**

<img width="1362" height="252" alt="image" src="https://github.com/user-attachments/assets/ac2ba5a2-96a4-44c5-ba75-dd5ccf5a6d80" />


**Question 4**
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table name type

product_id INT product_name VARCHAR(10) category VARCHAR(50) cost_price DECIMAL(10) sell_price DECIMAL(10) reorder_lvl INT quantity INT supplier_id INT
---
sql
```
UPDATE Products
SET reorder_lvl = ROUND(reorder_lvl * 1.3)
WHERE cATEGORY = 'Food'
AND quantity < 0.5 * reorder_lvl;
```

**Output:**

<img width="1285" height="235" alt="image" src="https://github.com/user-attachments/assets/760cf3a4-4a48-47c0-a2d0-3b180fe1b041" />


**Question 5**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id
---
sql
```
UPDATE Employees
SET first_name = 'John'
WHERE department_id = 80
AND commission_pct < 0.35;
```

**Output:**

<img width="1353" height="223" alt="image" src="https://github.com/user-attachments/assets/1c9f9730-f63e-40cf-8989-a14106771f77" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
|CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 |
---
sql
```
DELETE FROM Customer 
WHERE GRADE = 2;
```

**Output:**

<img width="703" height="495" alt="image" src="https://github.com/user-attachments/assets/11691a93-2ceb-4f0d-a333-58effe93d913" />


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
|CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 |
---
sql
```
DELETE FROM Customer
WHERE GRADE <> 3;
```

**Output:**

<img width="598" height="412" alt="image" src="https://github.com/user-attachments/assets/9a811aa2-b4b2-4627-bb76-abc7829de890" />


**Question 8**
---
Write a SQL statement to Find the salesmen with all information who gets the commission within a range of 0.12 and 0.14.

salesman table

cid name type notnull dflt_value pk

0 salesman_id numeric(5) 0 1 1 name varchar(30) 0 0 2 city varchar(15) 0 0 3 commission decimal(5,2) 0 0
---
sql
```
SELECT *
FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

**Output:**

<img width="737" height="378" alt="image" src="https://github.com/user-attachments/assets/96bb0789-8fff-43f3-ac41-64bf441b3b1a" />


**Question 9**
---
Write a SQL query to determine the age group of value1 in the Calculations table as 'Child' if it is less than 13, 'Teen' if it is between 13 and 19, and 'Adult' if it is 20 or older.

cid name type notnull dflt_value pk

0 id INTEGER 0 1 1 value1 REAL 0 0 2 value2 REAL 0 0 3 base INTEGER 0 0 4 exponent INTEGER 0 0 5 number REAL 0 0 6 decimal REAL 0 0
---

sql
```
SELECT 
id, 
value1,
CASE
WHEN value1 < 13 THEN 'Child'
WHEN value1 BETWEEN 13 AND 19 THEN 'Teen'
ELSE 'Adult'
END AS age_group
FROM 
Calculations;
```

**Output:**

<img width="848" height="335" alt="image" src="https://github.com/user-attachments/assets/d7dbf5bb-d0a0-4b96-b5c6-e9cc0786660a" />


**Question 10**
---
Write a SQL query to find the details of those salespeople who live in cities other than Paris and Rome. Return salesman_id, name, city, commission.

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
-- 


sql
```
SELECT salesman_id, name, city, commission
FROM salesman
WHERE city NOT IN ('Paris', 'Rome');
```

**Output:**

<img width="818" height="337" alt="image" src="https://github.com/user-attachments/assets/aeb76a56-2c5b-43dc-8e14-e01cdf19cced" />

<img width="1497" height="278" alt="image" src="https://github.com/user-attachments/assets/06940ffb-5724-466e-a9d0-7de703fb6799" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
