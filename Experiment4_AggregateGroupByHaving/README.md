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
How many patients are there in each city?

```sql
SELECT Address, COUNT(*) AS TotalPatients FROM Patients GROUP BY Address;
```

**Output:**
--
<img width="453" height="308" alt="image" src="https://github.com/user-attachments/assets/ec314813-45db-4c32-a2f2-cb894dbe88c9" />



**Question 2**
---
How many medical records are there for each patient?

```sql
SELECT PatientID, COUNT(*) AS TotalRecords FROM MedicalRecords GROUP BY PatientID;
```

**Output:**
---
<img width="852" height="957" alt="image" src="https://github.com/user-attachments/assets/ce8e5315-321b-4e32-941e-5f61f75412c1" />



**Question 3**
---
Write a SQL Query to find how many medications are prescribed for each patient?

```sql
SELECT PatientID,count(*) AS AvgMedications FROM MedicalRecords GROUP BY PatientID;
```

**Output:**
---
<img width="798" height="779" alt="image" src="https://github.com/user-attachments/assets/df70dc59-48fc-4096-8f50-f27ca6147e16" />



**Question 4**
---
Write a SQL query to find Who has the highest income among employee living in California?

```sql
SELECT NAME,MAX(INCOME) AS 'max(income)' FROM employee WHERE city='California'
```

**Output:**
---
<img width="997" height="537" alt="image" src="https://github.com/user-attachments/assets/77ccf2a1-a71a-4890-b9c1-850490ffe126" />



**Question 5**
---
Write a SQL query to find the difference between the maximum and minimum price of fruits?

```sql
SELECT MAX(price) - MIN(price) AS price_diff FROM fruits;
```

**Output:**
---
<img width="319" height="301" alt="image" src="https://github.com/user-attachments/assets/81cb7737-462f-45a2-b43b-5a877fa01a17" />



**Question 6**
---
Write a SQL query to find the minimum purchase amount.

```sql
SELECT MIN(purch_amt) AS MINIMUM FROM orders;
```

**Output:**
---
<img width="317" height="300" alt="image" src="https://github.com/user-attachments/assets/f69d55e1-26a8-4c6b-acb0-50825ead3ced" />



**Question 7**
---
Write a SQL query to count the number of customers. Return number of customers.

```sql
SELECT COUNT(*) AS COUNT FROM customer;
```

**Output:**
---
<img width="380" height="358" alt="image" src="https://github.com/user-attachments/assets/53751c76-65fc-453a-9f73-49a144b80597" />



**Question 8**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

```sql
SELECT age, SUM(income) AS "SUM(income)" FROM employee GROUP BY age HAVING SUM(income) > 1000000;
```

**Output:**
---
<img width="920" height="668" alt="image" src="https://github.com/user-attachments/assets/31eb517b-caaf-4c58-8ebc-49c83e444aba" />



**Question 9**
---
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

```sql
SELECT category_id,count(*) AS 'COUNT' FROM products WHERE  category_id > 2 GROUP BY category_id;
```

**Output:**
---
<img width="617" height="368" alt="image" src="https://github.com/user-attachments/assets/317f8f11-1de9-45cf-ba36-c22e9fc81bc4" />



**Question 10**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

```sql
SELECT ADDRESS,SUM(SALARY) AS 'SUM(salary)' FROM CUSTOMER1 GROUP BY ADDRESS HAVING SUM(SALARY) > 2000;
```

**Output:**
---
<img width="902" height="775" alt="image" src="https://github.com/user-attachments/assets/473467e5-b885-490b-90fe-5895f8485e4a" />




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
