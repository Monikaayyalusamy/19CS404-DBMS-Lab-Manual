# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
-- 

```sql
UPDATE Products 
SET sell_price = CAST(cost_price * 1.35 AS INT)
WHERE ((sell_price - cost_price) / sell_price) * 100 < 30;
```

**Output:**

<img width="1246" height="277" alt="image" src="https://github.com/user-attachments/assets/6a075db9-4e4c-46b3-ac3b-63ad1649776b" />


**Question 2**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
--

```sql
UPDATE Employees
SET salary = salary + 500,
email = 'updated'
WHERE job_id = 'SA_REP'
AND commission_pct > 0.15;
```

**Output:**

<img width="1310" height="382" alt="image" src="https://github.com/user-attachments/assets/c7ca8ca2-d72f-44e1-b518-bae8b87fba25" />


**Question 3**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
--

```sql
UPDATE Suppliers 
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**

<img width="1362" height="252" alt="image" src="https://github.com/user-attachments/assets/d9d3b1e4-71a1-4917-899f-8442fae37e08" />


**Question 4**
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
--

```sql
UPDATE Products
SET reorder_lvl = ROUND(reorder_lvl * 1.3)
WHERE cATEGORY = 'Food'
AND quantity < 0.5 * reorder_lvl;
```

**Output:**

<img width="1285" height="235" alt="image" src="https://github.com/user-attachments/assets/41189583-4d4d-4c4e-883f-0c35a3b63692" />


**Question 5**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
--
```sql
UPDATE Employees
SET first_name = 'John'
WHERE department_id = 80
AND commission_pct < 0.35;
```

**Output:**

<img width="1353" height="223" alt="image" src="https://github.com/user-attachments/assets/54cc8303-9a7b-45b4-b88a-10486bef0df9" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
-- 

```sql
DELETE FROM Customer 
WHERE GRADE = 2;
```

**Output:**
<img width="703" height="495" alt="image" src="https://github.com/user-attachments/assets/d3c64224-8cb1-4262-bd40-4a94faf144a8" />

**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
-- 

```sql
DELETE FROM Customer
WHERE GRADE <> 3;
```

**Output:**

<img width="598" height="412" alt="image" src="https://github.com/user-attachments/assets/5f4a74d1-bdbd-4b80-8d7f-e097a0d5eca6" />


**Question 8**
---
Write a SQL statement to Find the salesmen with all information who gets the commission within a range of 0.12 and 0.14.

salesman table

cid         name         type        notnull     dflt_value  pk
----------  -----------  ----------  ----------  ----------  ----------
0           salesman_id  numeric(5)    0                       1
1           name         varchar(30)   0                       0
2           city         varchar(15)   0                       0
3           commission   decimal(5,2)  0                       0
                                                             
-- 

```sql
SELECT *
FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

**Output:**

<img width="737" height="378" alt="image" src="https://github.com/user-attachments/assets/d48f3ccc-6cb4-4965-9e29-41763509b003" />


**Question 9**
---
Write a SQL query to determine the age group of value1 in the Calculations table as 'Child' if it is less than 13, 'Teen' if it is between 13 and 19, and 'Adult' if it is 20 or older.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
-- 

```sql
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
<img width="848" height="335" alt="image" src="https://github.com/user-attachments/assets/c0224d7e-b41f-4087-9a10-1d350fff804d" />


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

```sql
SELECT salesman_id, name, city, commission
FROM salesman
WHERE city NOT IN ('Paris', 'Rome');
```

**Output:**

<img width="818" height="337" alt="image" src="https://github.com/user-attachments/assets/258dd215-f860-443f-97bb-7072331cc5b2" />

<img width="1497" height="278" alt="image" src="https://github.com/user-attachments/assets/bb17dd78-8608-43ec-bb34-f7dbdc1d9eb4" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
