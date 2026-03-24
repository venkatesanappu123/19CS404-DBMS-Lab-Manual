# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--

<img width="1194" height="735" alt="image" src="https://github.com/user-attachments/assets/a0d1f83b-bff7-4134-9d3d-69cb764197d3" />


```sql
select t1.student_name, t1.grade from GRADES t1
JOIN (
    SELECT subject, max(grade) as max_grade
    from GRADES
    GROUP BY subject
) t2
on t1.subject=t2.subject and t1.grade=t2.max_grade;
```

**Output:**

<img width="1199" height="554" alt="image" src="https://github.com/user-attachments/assets/873d786c-655c-4879-92e2-75f6c4d1677a" />

**Question 2**
---

<img width="1190" height="770" alt="image" src="https://github.com/user-attachments/assets/f65cfaa7-2cb4-4211-9806-6743230620c5" />


```sql
select * from Employee
where age < (select avg(age) from Employee
where income>250000);
```

**Output:**

<img width="1205" height="660" alt="image" src="https://github.com/user-attachments/assets/1f388d3a-4711-4968-a7eb-3ba8aa0c2e3d" />

**Question 3**
---

<img width="1198" height="725" alt="image" src="https://github.com/user-attachments/assets/374b15c7-4701-4a21-aa03-677a5375642a" />

```sql
select t.student_name, t.grade from GRADES t
JOIN (
    SELECT subject , min(grade) as min_grade from GRADES
    GROUP BY subject
) t2
ON t.subject=t2.subject and t.grade=t2.min_grade;
```

**Output:**

<img width="1198" height="558" alt="image" src="https://github.com/user-attachments/assets/3a544e61-7ac6-4efb-863c-ddb857f9c694" />

**Question 4**
---

<img width="1197" height="616" alt="image" src="https://github.com/user-attachments/assets/44dd4c70-c23c-4a61-a126-c42eb2ea5238" />


```sql
select t.* from customer t
JOIN (
    select city,max(id) from customer
    
) t2
on t.city != t2.city;
```

**Output:**

<img width="1198" height="628" alt="image" src="https://github.com/user-attachments/assets/4db1d143-cca0-4c38-b554-ecb731452405" />

**Question 5**
---

<img width="1198" height="539" alt="image" src="https://github.com/user-attachments/assets/742ca414-40de-4815-88f2-998ba2465cf4" />


```sql
select medication_id as medic, medication_name, dosage from Medications 
where dosage = (select min(dosage) from Medications);
```

**Output:**

<img width="1194" height="519" alt="image" src="https://github.com/user-attachments/assets/a2579b68-82a8-487b-bffa-f5bb904ad307" />

**Question 6**
---

<img width="1196" height="654" alt="image" src="https://github.com/user-attachments/assets/f8ef7e35-cfe6-468f-a4b6-2a20d8c9cc4a" />


```sql
select t.name from customer t
join (
    select phone,count(id),name from customer
    group by phone
    having count(id)=1
) t2
on t.name=t2.name;
```

**Output:**

<img width="1194" height="582" alt="image" src="https://github.com/user-attachments/assets/1c0e4342-dea6-4c95-9ba8-fc23ea128913" />

**Question 7**
---

<img width="1199" height="561" alt="image" src="https://github.com/user-attachments/assets/91470fb5-facc-426a-9cf4-78b1f678f3d5" />


```sql
select t1.ord_no, t1.purch_amt, t1.ord_date, t1.salesman_id from orders t1
JOIN (
    select salesman_id, max(commission) from salesman
) t2
on t1.salesman_id=t2.salesman_id;
```

**Output:**

<img width="1199" height="608" alt="image" src="https://github.com/user-attachments/assets/c6f9feb1-3d40-4df2-8d85-2c4e56f535d0" />

**Question 8**
---

<img width="1200" height="712" alt="image" src="https://github.com/user-attachments/assets/c711f35d-2cdf-49bf-b58f-cec6111b6660" />


```sql
select * from Orders
where salesman_id in (select salesman_id from Salesman where name = 'Paul Adam');
```

**Output:**

<img width="1198" height="534" alt="image" src="https://github.com/user-attachments/assets/af0ae023-3ad9-43aa-b2a2-f3b3859a848c" />

**Question 9**
---

<img width="1195" height="751" alt="image" src="https://github.com/user-attachments/assets/5add1f1c-ecb9-4ecd-a402-efb54c61327b" />


```sql
select * from CUSTOMERS
WHERE SALARY <2500;
```

**Output:**

<img width="1199" height="594" alt="image" src="https://github.com/user-attachments/assets/5f3703ad-3b1a-489a-80bd-89831b6f8ae8" />

**Question 10**
---

<img width="1198" height="745" alt="image" src="https://github.com/user-attachments/assets/9dd97949-67a6-4e5c-812a-e60d069253d2" />


```sql
select commission from salesman
where salesman_id in (select salesman_id from customer
where city = 'Paris');
```

**Output:**

<img width="1197" height="453" alt="image" src="https://github.com/user-attachments/assets/570079f7-08fb-4d00-9e83-d5f4da3da01b" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
