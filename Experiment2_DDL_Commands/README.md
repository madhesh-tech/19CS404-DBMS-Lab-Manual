# Experiment 2: DDL Commands
# Name : MADHESH I
# Reg No : 212224220055
## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```
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
```
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```
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
--
Insert all customers from Old_customers into Customers
Table attributes are CustomerID, Name, Address, Email

```sql
INSERT INTO Customers(CustomerID,Name,Address,Email)
SELECT CustomerID,Name,Address,Email FROM old_customers;
```

**Output:**

<img width="1234" height="364" alt="Screenshot 2025-09-27 082537" src="https://github.com/user-attachments/assets/7b1561c1-86c0-46e9-975c-84d33885f89b" />


**Question 2**
---
Create a table named Departments with the following columns:
DepartmentID as INTEGER
DepartmentName as TEXT

```sql
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**

<img width="1222" height="442" alt="Screenshot 2025-09-27 082710" src="https://github.com/user-attachments/assets/b50d8417-34a2-4496-8528-d4d4b00f8902" />


**Question 3**
---
Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.

```sql
ALTER TABLE Student_details add column MobileNumber NUMBER ;
alter table Student_details add column Address VARCHAR(100);
```

**Output:**
<img width="1228" height="467" alt="image" src="https://github.com/user-attachments/assets/e9be356e-e289-42bf-be80-8ed7a2613427" />


**Question 4**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:

```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK(Amount>0),
DueDate DATE CHECK(DueDate>InvoiceDate),
OrderID INTEGER,
FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**



**Question 5**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

```sql
INSERT INTO Books (ISBN, Title,Author,Publisher,Year)
VALUES('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

<img width="1219" height="316" alt="image" src="https://github.com/user-attachments/assets/493f9db9-df20-40fa-a85e-2ddb5d02537c" />


**Question 6**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
CREATE TABLE jobs(
job_id INT,
job_title VARCHAR(225) DEFAULT ' ',
min_salary INT DEFAULT 8000,
max_salary INT DEFAULT NULL
);
```

**Output:**

<img width="1222" height="409" alt="Screenshot 2025-09-27 083131" src="https://github.com/user-attachments/assets/f919d39c-7623-4bd5-b799-ed393f1d1f88" />


**Question 7**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```sql
CREATE TABLE Products(
ProductID INT PRIMARY KEY,
ProductName VARCHAR(255) NOT NULL,
Price REAL CHECK (Price>0),
Stock INT CHECK (Stock>=0)
);
```

**Output:**

<img width="1222" height="347" alt="Screenshot 2025-09-27 083254" src="https://github.com/user-attachments/assets/8f4c5056-ac18-4e67-954b-f8f3ac3513fb" />


**Question 8**
---
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300

```sql
INSERT INTO Products(Name,Category,Price,Stock)
VALUES('Smartphone','Electronics',800,150),('Headphones','Accessories',200,300);
```

**Output:**

<img width="1231" height="422" alt="Screenshot 2025-09-27 083515" src="https://github.com/user-attachments/assets/2395632c-ff70-4355-903a-60a0fece9cb9" />


**Question 9**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,item_desc TEXT NOT NULL,rate INTEGER NOT NULL,icom_id TEXT(4),FOREIGN KEY(icom_id)
REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**Output:**

<img width="1233" height="431" alt="Screenshot 2025-09-27 083631" src="https://github.com/user-attachments/assets/d301f7a7-8837-4b85-9a63-6cc76880367a" />


**Question 10**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
designation as VARCHAR(50)
net_salary as NUMBER
dob as DATE

```sql
ALTER TABLE Companies add designation varchar(50) ;
ALTER TABLE Companies add net_salary number;
ALTER TABLE Companies add dob date;
```

**Output:**

<img width="1244" height="509" alt="Screenshot 2025-09-27 083742" src="https://github.com/user-attachments/assets/6eac2730-ae19-4f23-9644-90275e249e54" />

**Grade:**
<img width="1330" height="228" alt="Screenshot 2025-09-27 084249" src="https://github.com/user-attachments/assets/d45da985-4592-4c41-8a9e-0a8dcdcd77e0" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
