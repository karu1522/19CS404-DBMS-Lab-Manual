# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.

```sql
SELECT c.cust_name, o.ord_no, o.ord_date, o.purch_amt
FROM customer c
LEFT JOIN orders o 
ON c.customer_id = o.customer_id;
```

**Output:**
---
<img width="1023" height="923" alt="image" src="https://github.com/user-attachments/assets/68509154-46f9-4796-b237-3b0acf6152b2" />


**Question 2**
---
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.

```sql
SELECT n.nurse_id, d.department_name
FROM nurses n
INNER JOIN departments d ON n.department_id = d.department_id
WHERE n.first_name = 'David' AND n.last_name = 'Moore';
```

**Output:**
---
<img width="1020" height="563" alt="image" src="https://github.com/user-attachments/assets/e043358f-eb7e-44b2-8b1b-b047c9c207f2" />


**Question 3**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.

```sql
SELECT p.*, d.specialization AS doctor_specialization
FROM patients p
INNER JOIN doctors d ON p.doctor_id = d.doctor_id;
```

**Output:**
---
<img width="1690" height="366" alt="image" src="https://github.com/user-attachments/assets/aad60a14-44ca-4f15-bdcc-154eade141f2" />


**Question 4**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
SELECT c.cust_name, c.city AS "city", c.grade, s.name AS "Salesman", s.city AS "city"
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```

**Output:**
---
<img width="1449" height="719" alt="image" src="https://github.com/user-attachments/assets/a5095ed4-5fd3-42d9-9c66-a9588a502d99" />


**Question 5**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.

```sql
SELECT c.cust_name AS "Customer Name", c.city, s.name AS "Salesman", s.city, s.commission
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city 
AND s.commission > 0.12;
```

**Output:**
---
<img width="1549" height="622" alt="image" src="https://github.com/user-attachments/assets/680dd590-fb6b-4427-b72a-fbbe94f85c04" />


**Question 6**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM orders o
JOIN customer c 
    ON o.customer_id = c.customer_id
JOIN salesman s 
    ON o.salesman_id = s.salesman_id;
```

**Output:**
---
<img width="1703" height="801" alt="image" src="https://github.com/user-attachments/assets/11d1a7ba-190e-4dd7-9825-0747b2d3c9e2" />


**Question 7**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

```sql
SELECT s.name, c.cust_name, c.city, c.grade, c.salesman_id
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE s.salesman_id IN (
    SELECT salesman_id 
    FROM customer 
    GROUP BY salesman_id 
    HAVING COUNT(customer_id) > 1
);
```

**Output:**
---
<img width="1604" height="637" alt="image" src="https://github.com/user-attachments/assets/2f8c876b-caca-4aeb-9ac8-24e44e9dfc6d" />


**Question 8**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

```sql
SELECT c.cust_name, c.city, c.grade, s.name AS "Salesman", s.city
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**
---
<img width="1459" height="864" alt="image" src="https://github.com/user-attachments/assets/720db9a4-879f-43d6-bd8e-d2cdfdce1ad0" />


**Question 9**
---
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```sql
SELECT c.cust_name AS "Customer Name", c.city, s.name AS "Salesman", s.commission
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
```

**Output:**
---
<img width="1259" height="723" alt="image" src="https://github.com/user-attachments/assets/0bad3bf9-24fc-466c-8210-56ad6cf47238" />


**Question 10**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a null discharge date.

```sql
SELECT p.first_name AS patient_name, d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NULL;
```

**Output:**
---
<img width="933" height="611" alt="image" src="https://github.com/user-attachments/assets/64da5efd-46d6-4066-ad31-5fb3d66fe051" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
