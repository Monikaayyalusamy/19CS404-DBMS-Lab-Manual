# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

### Program:
![image](https://github.com/user-attachments/assets/449ef46d-2042-4796-9f6e-93f46970c6d3)


**Expected Output:**  
Greater number is: 80

### Output:
![image](https://github.com/user-attachments/assets/1bcb42fa-d63e-4082-ba4d-4fe0f83fba8b)
---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

### Program:
![image](https://github.com/user-attachments/assets/5504a8aa-528c-4f2d-bf34-43eaa261eed6)

**Expected Output:**  
Sum of first 10 natural numbers is: 55

### Output:
![image](https://github.com/user-attachments/assets/d1de6671-c100-4f59-b958-d9d6ff514321)

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

### Program:
![image](https://github.com/user-attachments/assets/948ee7a6-775f-4ea0-9b6b-ea631ae627dd)


**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

 ### Output
 ![image](https://github.com/user-attachments/assets/dcd3e413-28af-4fe0-a993-18395e64a825)

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

### Program:
![image](https://github.com/user-attachments/assets/4a4ad415-132f-471f-9c00-bcd186c7f665)

**Expected Output:**  
n = 1535  
Reversed number is 5351

### Output:
![image](https://github.com/user-attachments/assets/1fbdbeff-b0b6-462f-a36b-67126a101ea2)

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

### Program:
![image](https://github.com/user-attachments/assets/20e400fb-a09d-45b1-b8fa-1496fd4ca8b5)

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

### Output:
![image](https://github.com/user-attachments/assets/17454c07-8a8f-46f9-9c5a-318ac1b5aeb6)

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
