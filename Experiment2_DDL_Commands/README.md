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
--
<img width="1206" height="446" alt="image" src="https://github.com/user-attachments/assets/988832c6-dfa4-4beb-b019-7564088320d8" />

```sql
CREATE TABLE Locations(
    LocationID INTEGER,
    LocationName TEXT,
    Address TEXT
);
```

**Output:**

<img width="1207" height="505" alt="image" src="https://github.com/user-attachments/assets/2a25a8d3-4e6d-43c8-a358-9d85acb86ef6" />

**Question 2**
---

<img width="1200" height="532" alt="image" src="https://github.com/user-attachments/assets/5bca8666-a428-43ff-94bc-ec2cc97b2991" />

```sql
INSERT INTO Student_details 
SELECT * FROM Archived_students;

```

**Output:**

<img width="1204" height="410" alt="image" src="https://github.com/user-attachments/assets/856c031c-9db4-41f7-b99d-d7b6ebcc55ab" />

**Question 3**
---

<img width="1195" height="453" alt="image" src="https://github.com/user-attachments/assets/b118fdc8-0a51-4cde-8fa0-23bc3f258e60" />

```sql
CREATE TABLE Members(
    MemberID INTEGER,
    MemberName TEXT,
    JoinDate DATE
);
```

**Output:**

<img width="1201" height="503" alt="image" src="https://github.com/user-attachments/assets/41078816-fbcc-4284-aa71-e051c398b271" />

**Question 4**
---

<img width="1201" height="554" alt="image" src="https://github.com/user-attachments/assets/d737e0a2-8049-4be9-86dc-4450b654957b" />

```sql
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode) VALUES
(306,"Diana Prince","Themyscira",NULL,NULL),
(307,"Bruce Wayne","Wayne Mano","Gotham",10007),
(308,"Peter Parker","Queens",NULL,11375);
```

**Output:**

<img width="1203" height="411" alt="image" src="https://github.com/user-attachments/assets/36e34b42-53d1-4d21-8b44-c4f016b60f6d" />

**Question 5**
---

<img width="1201" height="489" alt="image" src="https://github.com/user-attachments/assets/d01ab06f-2b99-4ac3-b95b-23f5a4e1ce6f" />

```sql
INSERT INTO Customers(CustomerID,Name,Address) values (304,"Peter Parker","Spider St");
```

**Output:**

<img width="1202" height="451" alt="image" src="https://github.com/user-attachments/assets/3f56b525-b3ef-4cc4-950b-39796aeb5aed" />

**Question 6**
---

<img width="1204" height="447" alt="image" src="https://github.com/user-attachments/assets/52f12f90-ef2e-4d40-9301-b469d9a60cc2" />

```sql
ALTER TABLE Employees
ADD salary INTEGER CHECK(salary>0);
```

**Output:**

<img width="1202" height="410" alt="image" src="https://github.com/user-attachments/assets/c3bb5696-fdd7-4e8a-b57b-355cba701304" />

**Question 7**
---

<img width="1201" height="399" alt="image" src="https://github.com/user-attachments/assets/ff0f540d-48ac-489f-8949-8ec32386bcee" />

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY(ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1195" height="393" alt="image" src="https://github.com/user-attachments/assets/7fa2de2f-b6a0-44d6-b9d9-2157de4f6fcc" />

**Question 8**
---

<img width="1201" height="513" alt="image" src="https://github.com/user-attachments/assets/2eece4a8-a230-4141-b827-c8723206540f" />

```sql
CREATE TABLE item(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHECK(length(icom_id)=4),
    FOREIGN KEY(icom_id) REFERENCES company(com_id)
    ON UPDATE CASCADE
    ON DELETE CASCADE
);
```

**Output:**

<img width="1195" height="476" alt="image" src="https://github.com/user-attachments/assets/29a7daae-8a16-4dc4-8855-de7c1de122c8" />

**Question 9**
---

<img width="1201" height="475" alt="image" src="https://github.com/user-attachments/assets/9502bd05-626b-4fc0-80cf-d042fc649fcf" />

```sql
ALTER TABLE employee
RENAME COLUMN id TO employee_id;
```

**Output:**

<img width="1207" height="375" alt="image" src="https://github.com/user-attachments/assets/f885d3f2-0f37-4f33-908d-9c44dd6cdc68" />

**Question 10**
---

<img width="1207" height="480" alt="image" src="https://github.com/user-attachments/assets/d93c33a5-b83b-4d97-bd90-576022ce9e2f" />

```sql
CREATE TABLE contacts(
    contact_id integer primary key,
    first_name text not null,
    last_name text not null,
    email text,
    phone text not null check(length(phone)>=10)
);
```

**Output:**

<img width="1206" height="442" alt="image" src="https://github.com/user-attachments/assets/d2e5ee26-1cc2-4352-b44c-c6439dc58864" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
