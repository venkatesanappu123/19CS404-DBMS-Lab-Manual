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

<img width="1207" height="672" alt="image" src="https://github.com/user-attachments/assets/687c4b1c-ea33-4c9b-8538-3f47c6f217aa" />

```sql
SELECT customer_id, cust_name, city, grade, salesman_id FROM customer WHERE grade IS NULL;
```

**Output:**

<img width="1202" height="548" alt="image" src="https://github.com/user-attachments/assets/1216b7f5-255e-4837-87d8-20993651a328" />

**Question 2**
---

<img width="1203" height="354" alt="image" src="https://github.com/user-attachments/assets/e4d016a9-1325-440d-a5a8-692fb9beada2" />

```sql
UPDATE Products
SET sell_price=sell_price*1.1
WHERE category = "Bakery";
```

**Output:**

<img width="1208" height="659" alt="image" src="https://github.com/user-attachments/assets/b2238684-9cb3-42f0-a523-17a75469af8b" />

**Question 3**
---

<img width="1206" height="718" alt="image" src="https://github.com/user-attachments/assets/728d4cf9-b8fe-4b45-bcc2-5a831edd9274" />


```sql
UPDATE Employees
SET salary=salary*2
WHERE job_id LIKE '%MAN';

```

**Output:**

<img width="1198" height="465" alt="image" src="https://github.com/user-attachments/assets/7b204445-25e8-4281-b0e7-2ac32d6bc9ba" />

**Question 4**
---

<img width="1202" height="631" alt="image" src="https://github.com/user-attachments/assets/bf49425f-992a-4b63-a6ce-de55330ba75e" />

```sql
UPDATE Products
SET sell_price=sell_price*1.15
WHERE quantity < 50 AND supplier_id = 10;

```

**Output:**

<img width="1209" height="626" alt="image" src="https://github.com/user-attachments/assets/9024f926-259a-40b6-82f0-e5753c5a931e" />

**Question 5**
---

<img width="1189" height="602" alt="image" src="https://github.com/user-attachments/assets/b96d215f-c6f6-406d-bc88-1b67742a9343" />


```sql
select EmpFname || " " || EmpLname as FullName from EmployeeInfo;

```

**Output:**

<img width="1207" height="442" alt="image" src="https://github.com/user-attachments/assets/ebdade1a-513d-42b4-a632-1a196b125018" />

**Question 6**
---

<img width="1199" height="686" alt="image" src="https://github.com/user-attachments/assets/9bb50d80-cc27-4bd6-9eed-31e94974ec9f" />

```sql
select salesman_id,name,city,commission from salesman
where city not in ('Paris','Rome');
```

**Output:**

<img width="1200" height="500" alt="image" src="https://github.com/user-attachments/assets/fc8ba10e-5fd1-4a00-8031-ba762ddf6051" />

**Question 7**
---

<img width="1185" height="690" alt="image" src="https://github.com/user-attachments/assets/4ac9a6e0-eb76-452f-b473-7049499e1d6a" />

```sql
select * from emp
where hiredate between "2022-01-01" and "2022-12-31";
```

**Output:**

<img width="1200" height="471" alt="image" src="https://github.com/user-attachments/assets/fcc5fd67-44be-4962-aeae-1d80627ba852" />

**Question 8**
---

<img width="1206" height="592" alt="image" src="https://github.com/user-attachments/assets/6218be36-f01f-4e76-bf3d-469280778ecf" />

```sql
UPDATE products
set reorder_lvl =reorder_lvl*1.3
where category='Food' and quantity < 0.5*reorder_lvl;
```

**Output:**

<img width="1201" height="528" alt="image" src="https://github.com/user-attachments/assets/a472fee8-9b9a-4970-be30-127550fb7088" />

**Question 9**
---

<img width="1207" height="540" alt="image" src="https://github.com/user-attachments/assets/7c4692ae-8b53-47b8-bb86-4513e3cb501e" />

```sql
Delete from Customer
where GRADE%2!=0;
```

**Output:**

<img width="1205" height="545" alt="image" src="https://github.com/user-attachments/assets/ae29358f-d0bb-4623-836c-3f53ead0a813" />

**Question 10**
---

<img width="1212" height="755" alt="image" src="https://github.com/user-attachments/assets/839b9f43-f9a2-4cb2-94e8-03c19997fda0" />

```sql
Update emp
set hiredate='1981-11-17'
where ename='TURNER';
select ename, cast((julianday('2024-08-30')-julianday(hiredate))/365 as INTEGER) AS Tenure
from emp;
```

**Output:**

<img width="1206" height="497" alt="image" src="https://github.com/user-attachments/assets/b0892dae-b8b6-4eff-b687-d312c4b6c4fe" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
