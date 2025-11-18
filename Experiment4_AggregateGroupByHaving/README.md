# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many patients have insurance coverage valid in each year?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT
-- 

```sql
SELECT
    SUBSTR(ValidityPeriod,1,4) AS ValidityYear,
    COUNT(DISTINCT PatientID) AS TotalPatients
FROM
    Insurance
GROUP BY
    ValidityYear;
```

**Output:**

<img width="780" height="371" alt="image" src="https://github.com/user-attachments/assets/475d13d4-2554-43e3-82f7-6b9338f2e5c2" />


**Question 2**
---
How many doctors specialize in each medical specialty?

Sample table:Doctors Table

<img width="1039" height="162" alt="image" src="https://github.com/user-attachments/assets/de6b9998-5d24-40e0-8be4-139334f872c6" />

-- 

```sql
SELECT Specialty,COUNT(DoctorID) AS TotalDocto
FROM Doctors
GROUP BY Specialty;
```

**Output:**

<img width="598" height="633" alt="image" src="https://github.com/user-attachments/assets/e948656e-51a7-47b4-8fad-5768dbafca01" />


**Question 3**
---
How many medical records were created in each month?

Sample table:MedicalRecords Table
<img width="1089" height="164" alt="image" src="https://github.com/user-attachments/assets/f355ca55-e03d-48db-9730-1a233fea36f8" />

--

```sql
SELECT
    strftime('%Y-%m',Date) AS Month, 
    COUNT(*) AS TotalRecords
FROM 
    MedicalRecords
GROUP BY 
    Month;
```

**Output:**

<img width="652" height="443" alt="image" src="https://github.com/user-attachments/assets/544f99d2-921a-4afc-84d8-d1e3dbe8c420" />


**Question 4**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
-- 

```sql
SELECT COUNT(*) AS employees_count
FROM employee
WHERE income>50000;
```

**Output:**

<img width="452" height="342" alt="image" src="https://github.com/user-attachments/assets/9b0efad6-46a9-49ed-a80f-4e195e7abdc4" />


**Question 5**
---
Write a SQL query to find the Fruit with the lowest available quantity.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
-- 

```sql
SELECT name AS fruit_name,inventory AS lowest_quantity
FROM fruits
ORDER BY inventory ASC
LIMIT 1;
```

**Output:**

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/7f56ffce-8b47-4828-8173-383d63cd7037" />


**Question 6**
---
Write a SQL query to find Who has the highest income among employee living in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
-- 

```sql
SELECT name,max(income)
FROM employee
WHERE city='California'
ORDER BY income DESC
LIMIT 1;
```

**Output:**

<img width="542" height="323" alt="image" src="https://github.com/user-attachments/assets/323e36a2-5df8-40d6-b8de-08cdba2de5ef" />


**Question 7**
---
Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee

id

name

age

address

salary

1

Paul

32

California

20000

4

Mark

25

Richtown

65000

5

David

27

Texas

85000


-- 

```sql
SELECT COUNT(*) AS COUNT
FROM employee
WHERE age>32;
```

**Output:**

<img width="487" height="352" alt="image" src="https://github.com/user-attachments/assets/806f3863-7a6d-4793-9d4f-32ba9a234c49" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1
<img width="992" height="173" alt="image" src="https://github.com/user-attachments/assets/a48ca025-2516-4f55-b9b8-8f1da0c6a5c9" />

--

```sql
SELECT (age/5)*5 AS age_group,SUM(salary)
FROM customer1
GROUP BY (age/5)*5
HAVING SUM(salary)>5000;
```

**Output:**

<img width="651" height="378" alt="image" src="https://github.com/user-attachments/assets/6dfa9627-ad49-4062-a770-817a725f9e6b" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

Sample table: employee
<img width="1011" height="215" alt="image" src="https://github.com/user-attachments/assets/70967c08-f58f-4621-9d57-303b47eea1c4" />

-- 

```sql
SELECT city,AVG(income) AS 'AVG(income)'
FROM employee
GROUP BY city
HAVING AVG(income)>500000;
```

**Output:**

<img width="588" height="466" alt="image" src="https://github.com/user-attachments/assets/70e704f0-3852-44be-adc8-3941ff4cb559" />


**Question 10**
---
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

Sample table: customer1
<img width="992" height="173" alt="image" src="https://github.com/user-attachments/assets/8beab414-e9d5-453a-8834-6be6a13ae91c" />

-- 

```sql
SELECT address,AVG(salary)
FROM customer1
GROUP BY address
HAVING AVG(salary)<15000;
```

**Output:**
<img width="618" height="652" alt="image" src="https://github.com/user-attachments/assets/9b7a9ee8-271d-458b-84a0-f34a1bff7d85" />


<img width="1473" height="251" alt="image" src="https://github.com/user-attachments/assets/f7126c09-e731-467f-bbb6-8c8e42be9bbe" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
