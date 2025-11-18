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
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate. 
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
```sql
CREATE TABLE Invoices(
InvoiceID INTEGER,
InvoiceDate DATE,
Amount REAL CHECK(Amount>0),
DueDate DATE CHECK (Duedate>InvoiceDate),
OrderID INTEGER,
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1366" height="173" alt="image" src="https://github.com/user-attachments/assets/45d1380b-d11d-40e1-a8e3-f1a7c4ecdc1b" />


**Question 2**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql
INSERT INTO Customers(CustomerID,Name,Address,Email)
SELECT CustomerID,Name,Address,Email
from Old_customers;
```

**Output:**

<img width="875" height="166" alt="image" src="https://github.com/user-attachments/assets/cf1db992-c83b-4cbd-9e74-03f7e2f5898f" />


**Question 3**
---
Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values.

```sql
INSERT INTO Products(ProductID,Name,Category)
values(104,'Tablet','Electronics')
```

**Output:**

<img width="1307" height="230" alt="image" src="https://github.com/user-attachments/assets/5a515fcc-42e7-4e60-95b7-5ffd6a0f8238" />

**Question 4**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```sql
CREATE TABLE products(
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL(10,2) NOT NULL,
discount DECIMAL(10,2) DEFAULT 0 NOT NULL,
CHECK (list_price>=discount AND discount>=0 AND list_price>=0)
);
```

**Output:**

<img width="1388" height="175" alt="image" src="https://github.com/user-attachments/assets/7fa39bf2-59f4-4b3e-acd5-b6d009ec0c67" />

**Question 5**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT

```sql
INSERT INTO Employee(EmployeeID, Name,Position,Department,Salary)
VALUES(5,'George Clark','Consultant',NULL,NULL);
INSERT INTO Employee(EmployeeID, Name,Position,Department,Salary) 
VALUES(7,'Noah Davis','Manager','HR',60000);
INSERT INTO Employee(EmployeeID, Name,Position,Department,Salary) 
VALUES(8,'Ava Miller','Consultant','IT',NULL);
```

**Output:**

<img width="1285" height="282" alt="image" src="https://github.com/user-attachments/assets/5bfff43c-bfa8-4c9d-9d28-f56fa5ca37e8" />


**Question 6**
---
Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

 

```sql
ALTER TABLE Employee
ADD COLUMN department_id INTEGER;
ALTER TABLE Employee
ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**

<img width="1273" height="211" alt="image" src="https://github.com/user-attachments/assets/c1dfa2b9-20a8-4749-8366-bc99073f9ae9" />


**Question 7**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY (supplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));
```

**Output:**

<img width="1322" height="210" alt="image" src="https://github.com/user-attachments/assets/b80b59ba-d6ec-420c-b12e-46f083c97570" />


**Question 8**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.


```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
DueDate DATE CHECK (DueDate>InvoiceDate),
Amount REAL CHECK (Amount>0));
```

**Output:**

<img width="1298" height="285" alt="image" src="https://github.com/user-attachments/assets/5c27619a-83ab-46b4-892a-d8cd5eac1eef" />


**Question 9**
---
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
INSERT INTO Employee(EmployeeID,Name,Department,Salary)
SELECT EmployeeID,Name,Department,Salary 
FROM Former_employees;
```

**Output:**

<img width="1226" height="366" alt="image" src="https://github.com/user-attachments/assets/48558994-d25f-4d80-ac3e-ebf45aba7e22" />


**Question 10**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```sql
CREATE TABLE Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT);
```

**Output:**

<img width="1325" height="317" alt="image" src="https://github.com/user-attachments/assets/db78a63a-e995-46d2-b939-54db8b677912" />

<img width="1845" height="717" alt="image" src="https://github.com/user-attachments/assets/59a4aaf5-5262-4a8b-bff4-f30a67cf31d9" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
