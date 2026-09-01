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

### Code:
```
SELECT 'Greater number is: ' ||
       CASE
           WHEN 50 > 80 THEN 50
           ELSE 80
       END AS Result;
```

**Expected Output:**  


<img width="311" height="430" alt="image" src="https://github.com/user-attachments/assets/0432a3d9-51be-43b0-85bd-7fc6df87c579" />

Greater number is: 80

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

### Code:
```
WITH RECURSIVE numbers(n, total) AS (
    SELECT 1, 1
    UNION ALL
    SELECT n + 1, total + n + 1
    FROM numbers
    WHERE n < 10
)
SELECT 'Sum of first 10 natural numbers is: ' || total AS Result
FROM numbers
WHERE n = 10;
```

**Expected Output:**  


<img width="591" height="241" alt="image" src="https://github.com/user-attachments/assets/06deb5cf-e28c-4a18-84e4-8cc9df6b154d" />

Sum of first 10 natural numbers is: 55

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

### Code:
```
WITH RECURSIVE fibonacci(n, a, b) AS (
    SELECT 1, 0, 1
    UNION ALL
    SELECT n + 1, b, a + b
    FROM fibonacci
    WHERE n < 7
)
SELECT 'Fibonacci sequence: ' ||
       GROUP_CONCAT(a, ', ') AS Result
FROM fibonacci;
```

**Expected Output:**  

<img width="377" height="240" alt="image" src="https://github.com/user-attachments/assets/c0399a93-b15e-4593-969b-1072dc420162" />

n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

### Code:
```
WITH RECURSIVE reverse_num(n, rev) AS (
    SELECT 1535, 0
    UNION ALL
    SELECT n / 10, rev * 10 + (n % 10)
    FROM reverse_num
    WHERE n > 0
)
SELECT 'Reversed number is: ' || rev AS Result
FROM reverse_num
WHERE n = 0;
```

**Expected Output:**  

<img width="427" height="243" alt="image" src="https://github.com/user-attachments/assets/53efc58b-fb1b-4082-9555-6e96cb1d6c13" />

n = 1535  
Reversed number is 5351

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

### Code:
```
SELECT 'Largest of three numbers is: ' || MAX(10, 9, 15) AS Result;
```

**Expected Output:** 

<img width="621" height="95" alt="image" src="https://github.com/user-attachments/assets/b721cc71-1842-4e76-a2cd-cc9cae3f0db7" />

a = 10, b = 9, c = 15  
Largest of three number is 15

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
