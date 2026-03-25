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
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

```sql
UPDATE Products SET sell_price = sell_price * 1.15 WHERE quantity < 50 AND supplier_id = 10;
```

**Output:**
--
<img width="1663" height="338" alt="image" src="https://github.com/user-attachments/assets/a3fb5a34-dcf9-4ed4-8299-c591239f57a5" />



**Question 2**
---
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

```sql
UPDATE Products SET reorder_lvl = 20 WHERE quantity < 10 AND category = 'Snacks';
```

**Output:**
--
<img width="1633" height="387" alt="image" src="https://github.com/user-attachments/assets/29024a26-a82f-49ef-84ca-b3ed1e290109" />



**Question 3**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

```sql
UPDATE Employees SET email = 'not available', commission_pct = 0.55 WHERE department_id = 110;
```

**Output:**
--
<img width="1197" height="250" alt="image" src="https://github.com/user-attachments/assets/be0a2120-f49f-40ba-b6c7-190a68c73fa9" />



**Question 4**
---
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

```sql
UPDATE Products SET sell_price = CAST(sell_price *1.1 AS INT) WHERE supplier_id = 6;
```

**Output:**
--
<img width="1657" height="369" alt="image" src="https://github.com/user-attachments/assets/f47bb118-444f-4da9-aca7-badfa0f7ae8c" />



**Question 5**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

```sql
DELETE FROM customer WHERE grade >= 2;
```

**Output:**
--
<img width="465" height="385" alt="image" src="https://github.com/user-attachments/assets/bd8092f7-5c03-40fc-9eed-e7fcedb33cde" />



**Question 6**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.

```sql
DELETE FROM Surgeries WHERE surgery_id = 3 OR surgeon_id = 4;
```

**Output:**
--
<img width="866" height="636" alt="image" src="https://github.com/user-attachments/assets/01aa4825-e53f-44dd-b3dd-e08adab091a2" />



**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```sql
DELETE FROM customer WHERE GRADE <> 3;
```

**Output:**
--
<img width="468" height="367" alt="image" src="https://github.com/user-attachments/assets/9691c142-d27f-401d-8068-d4d5f5253a7a" />



**Question 8**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:
```sql
DELETE FROM Customer WHERE (GRADE > 2 AND PAYMENT_AMT < (SELECT AVG(PAYMENT_AMT) FROM Customer)) OR OUTSTANDING_AMT > 8000;
```

**Output:**
--
<img width="1853" height="398" alt="image" src="https://github.com/user-attachments/assets/60011fb9-886e-4eeb-b0d3-ba7bc303b320" />


**Question 9**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3
```sql
DELETE FROM Surgeries WHERE surgery_id = 3;
```

**Output:**
--
<img width="829" height="247" alt="image" src="https://github.com/user-attachments/assets/e38e3080-b9ad-4ad1-aa23-15ee2cd09458" />


**Question 10**
---
Write a query to Select all the records from the EmployeeInfo table, where the departments are either HR or Account.
```sql
SELECT * FROM Employeeinfo WHERE Department IN ('HR', 'Account');
```

**Output:**
--
<img width="1272" height="181" alt="image" src="https://github.com/user-attachments/assets/d17f21f0-0cee-4d83-9e16-e2ff8a3e84b5" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
