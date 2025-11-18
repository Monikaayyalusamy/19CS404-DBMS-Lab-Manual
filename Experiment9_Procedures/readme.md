# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

## Program
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE find_square (num IN NUMBER)
IS
    square_result NUMBER;
BEGIN
    -- Compute square
    square_result := num * num;
    
    -- Display the result
    DBMS_OUTPUT.PUT_LINE('Square of ' || num || ' is ' || square_result);
END;
/
```
```
BEGIN
    find_square(6);
END;
/
```

**Expected Output:**  
Square of 6 is 36

## Output
<img width="1009" height="665" alt="image" src="https://github.com/user-attachments/assets/cfaf01d8-277d-4144-83db-0296e61880af" />


---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

## Program
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE FUNCTION get_factorial(n IN NUMBER)
RETURN NUMBER
IS
    fact NUMBER := 1;
BEGIN
    IF n < 0 THEN
        RAISE_APPLICATION_ERROR(-20001, 'Factorial is not defined for negative numbers.');
    END IF;

    -- Loop to calculate factorial
    FOR i IN 1..n LOOP
        fact := fact * i;
    END LOOP;

    RETURN fact;
END;
/
```
```
BEGIN
    DBMS_OUTPUT.PUT_LINE('Factorial of 5 is ' || get_factorial(5));
END;
/
```

**Expected Output:**  
Factorial of 5 is 120

## Output
<img width="1022" height="666" alt="image" src="https://github.com/user-attachments/assets/bf1ca758-67ca-4f9f-8ead-f39d760ee9e5" />


---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

## Program
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE check_even_odd(num IN NUMBER)
IS
BEGIN
    IF MOD(num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(num || '  is  Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(num || '  is  Odd');
    END IF;
END;
/
BEGIN
    check_even_odd(12);
END;
/
```

**Expected Output:**  
12 is Even

## Output
<img width="1015" height="644" alt="image" src="https://github.com/user-attachments/assets/d1c2f05d-3be9-438b-8683-d54aa93a385d" />


---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

## Program
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE FUNCTION reverse_number(n IN NUMBER)
RETURN NUMBER
IS
    original_num NUMBER := n;
    reversed_num NUMBER := 0;
    digit NUMBER;
BEGIN
    WHILE original_num > 0 LOOP
        digit := MOD(original_num, 10);          -- Extract last digit
        reversed_num := reversed_num * 10 + digit;  -- Append digit
        original_num := TRUNC(original_num / 10);   -- Remove last digit
    END LOOP;

    RETURN reversed_num;
END;
/
```
```
BEGIN
    DBMS_OUTPUT.PUT_LINE('Reversed number of 1234 is ' || reverse_number(1234));
END;
/
```

**Expected Output:**  
Reversed number of 1234 is 4321

## Output
<img width="1022" height="627" alt="image" src="https://github.com/user-attachments/assets/001cce11-cf5a-4b5a-adb9-1cc78bb1f018" />


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

## Program
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE print_table(num IN NUMBER)
IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || num || ':');
    
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(num || ' x ' || i || ' = ' || (num * i));
    END LOOP;
END;
/
```
```
BEGIN
    print_table(5);
END;
/
```

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

## Output
<img width="1014" height="685" alt="image" src="https://github.com/user-attachments/assets/d9f3b5b2-abf6-49d0-bd29-59f9c8a57509" />


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
