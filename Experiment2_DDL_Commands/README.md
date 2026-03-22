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
---
Create a table named ProjectAssignments with the following constraints:
1. AssignmentID as INTEGER should be the primary key.
2. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
3. ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
4. AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**
<img width="1775" height="223" alt="image" src="https://github.com/user-attachments/assets/82f97c24-8080-4729-8c97-63f58fc5f599" />



**Question 2**
---
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 

```sql
ALTER TABLE Companies RENAME COLUMN name to first_name;
ALTER TABLE Companies ADD COLUMN mobilenumber number;
ALTER TABLE Companies ADD COLUMN DOB Date;
```

**Output:**
<img width="1064" height="230" alt="image" src="https://github.com/user-attachments/assets/205ac8d5-d854-488d-a3bf-385c88fcccfb" />



**Question 3**
---
Create a table named Tasks with the following columns:
1. TaskID as INTEGER
2. TaskName as TEXT
3. DueDate as DATE

```sql
CREATE TABLE Tasks (
    TaskID INTEGER,
    TaskName TEXT,
    DueDate DATE
);
```

**Output:**
<img width="1724" height="346" alt="image" src="https://github.com/user-attachments/assets/d6d348e0-4bea-450a-8579-34e07df3bf1b" />



**Question 4**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
INSERT INTO Employee (EmployeeID, Name, Position) VALUES (5, 'George Clark', 'Consultant');
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary) VALUES (7, 'Noah Davis', 'Manager', 'HR', 60000);
INSERT INTO Employee (EmployeeID, Name, Position, Department) VALUES (8, 'Ava Miller', 'Consultant', 'IT');
```

**Output:**
<img width="1647" height="308" alt="image" src="https://github.com/user-attachments/assets/f26862f3-3579-449a-a250-2b720a9a1dd2" />



**Question 5**
---
Create a table named Products with the following constraints:
1. ProductID should be the primary key.
2. ProductName should be NOT NULL.
3. Price is of real datatype and should be greater than 0.
4. Stock is of integer datatype and should be greater than or equal to 0.

```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName CHAR NOT NULL,
    Price REAL CHECK (Price > 0),
    Stock INTEGER CHECK (Stock >= 0)
);
```

**Output:**
<img width="1618" height="304" alt="image" src="https://github.com/user-attachments/assets/105df902-c34c-4553-bba6-0e0db79e6244" />



**Question 6**
---
Create a new table named item with the following specifications and constraints:
1. item_id as TEXT and as primary key.
2. item_desc as TEXT.
3. rate as INTEGER.
4. icom_id as TEXT with a length of 4.
5. icom_id is a foreign key referencing com_id in the company table.
8. The foreign key should cascade updates and deletes.
9. item_desc and rate should not accept NULL.

```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**Output:**
<img width="1425" height="310" alt="image" src="https://github.com/user-attachments/assets/4b2f54eb-923b-497c-8f6e-1a625ddbb8c2" />



**Question 7**
---
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

```sql
INSERT INTO Student_details (RollNo, Name, Gender) VALUES (204, 'Samuel Black', 'M');
```

**Output:**
<img width="1060" height="287" alt="image" src="https://github.com/user-attachments/assets/5c7d61a6-0f93-406b-8850-64aa0f52b9f0" />



**Question 8**
---
Insert all students from Archived_students table into the Student_details table.

```sql
INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
SELECT RollNo, Name, Gender, Subject, MARKS
FROM Archived_students;
```

**Output:**
<img width="1409" height="247" alt="image" src="https://github.com/user-attachments/assets/cd3c0db7-5f21-4cf1-a1c6-e2e7b49829f5" />



**Question 9**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
CREATE TABLE jobs (
    job_id INTEGER PRIMARY KEY,
    job_title TEXT DEFAULT NULL,
    min_salary INTEGER DEFAULT 8000,
    max_salary INTEGER NULL
);
```

**Output:**
<img width="1782" height="268" alt="image" src="https://github.com/user-attachments/assets/9401ab16-4c81-4627-9543-85445c7a344b" />



**Question 10**
---
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

```sql
ALTER TABLE Student_details ADD COLUMN mobilenumber number;
```

**Output:**
<img width="1683" height="332" alt="image" src="https://github.com/user-attachments/assets/2986d4b2-be96-44ee-b4af-37650188d67e" />




## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
