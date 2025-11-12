# Experiment 3: DML Commands
# Name : MADHESH I
# Reg No : 212224220055

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
Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.

```sql
update employees set salary=8000 where employee_id=105 and salary<5000;
```

**Output:**

<img width="1207" height="336" alt="Screenshot 2025-10-17 102851" src="https://github.com/user-attachments/assets/a45a2582-1945-472a-91ca-6671f91d601b" />


**Question 2**
---
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

```sql
update products set reorder_lvl=reorder_lvl*0.70 where cost_price > 50 and quantity<100;
```

**Output:**

<img width="1216" height="540" alt="Screenshot 2025-10-17 102958" src="https://github.com/user-attachments/assets/5efde9ab-b457-47db-8b7a-c33a8ac5d3f5" />



**Question 3**
---
Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules.

Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.

```sql
UPDATE employees
SET salary = CASE 
    WHEN department_id = 40  THEN CAST(ROUND(salary * 1.25, 0) AS INT)
    WHEN department_id = 90  THEN CAST(ROUND(salary * 1.15, 0) AS INT)
    WHEN department_id = 110 THEN CAST(ROUND(salary * 1.10, 0) AS INT)
    ELSE salary
END;
```

**Output:**
<img width="1920" height="1200" alt="Screenshot (44)" src="https://github.com/user-attachments/assets/3c5ac555-7900-4762-9330-5f541e8e8833" />

**Question 4**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

```sql
update suppliers set supplier_name='A1 Suppliers' where supplier_id = 8;
```

**Output:**
<img width="1238" height="505" alt="Screenshot (45)" src="https://github.com/user-attachments/assets/287fe31a-8da1-419e-b698-c35c2a5f8c9d" />

**Question 5**
---
For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

```sql
UPDATE sales
SET sell_price = sell_price + 3
WHERE product_id IN (
    SELECT product_id 
    FROM products 
    WHERE supplier_id = 4
);
```

**Output:**

<img width="1220" height="442" alt="Screenshot 2025-10-17 103638" src="https://github.com/user-attachments/assets/6effcafe-e848-4f48-983b-b7226968b4de" />


**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

```sql
delete from Customer where GRADE=2 and CUST_NAME LIKE 'M%' AND PAYMENT_AMT<3000;
```

**Output:**

<img width="1222" height="479" alt="Screenshot (46)" src="https://github.com/user-attachments/assets/23e47d51-7c4e-43a9-8d73-7b42a1ce2a6b" />


**Question 7**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

```sql
delete from Customer where GRADE=2 and CUST_NAME LIKE 'M%' AND PAYMENT_AMT<3000;
```

**Output:**



<img width="1920" height="1200" alt="Screenshot (48)" src="https://github.com/user-attachments/assets/aa575bc0-8813-4a1a-85fb-73d292760206" />



**Question 8**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

```sql
delete from Customer where (GRADE=3 or AGENT_CODE='A008') AND OUTSTANDING_AMT<5000;
```

**Output:**


<img width="1920" height="1200" alt="Screenshot (49)" src="https://github.com/user-attachments/assets/4cc22f45-2660-4e2d-a9a5-712ed37cc488" />

**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

```sql
delete from Customer where WORKING_AREA='New York';
```

**Output:**

<img width="1920" height="1200" alt="Screenshot (50)" src="https://github.com/user-attachments/assets/7cba51dd-56d4-4b63-9914-354f4c9c6852" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

```sql
delete from customer where GRADE>=2;
```

**Output:**


<img width="1920" height="1200" alt="Screenshot (51)" src="https://github.com/user-attachments/assets/8154d305-e586-429d-8767-d5f472c44feb" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
