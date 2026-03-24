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

<img width="1199" height="704" alt="image" src="https://github.com/user-attachments/assets/b48a2375-47c5-4544-9d22-1169dc551b1e" />


```sql
select p.first_name as patient_name , t.* from patients p
join test_results t
on p.patient_id=t.patient_id
where t.test_name='Blood Pressure';
```

**Output:**

<img width="1206" height="537" alt="image" src="https://github.com/user-attachments/assets/c00741c7-7f93-4526-a7b4-549a1e1e4421" />

**Question 2**
---

<img width="1199" height="718" alt="image" src="https://github.com/user-attachments/assets/497e6cbc-3bfe-4669-8fc2-1223acf37b89" />


```sql
select s.* from salesman s
left join customer c
on s.salesman_id=c.salesman_id
where c.cust_name='Fabian Johns';
```

**Output:**

<img width="1195" height="544" alt="image" src="https://github.com/user-attachments/assets/449bb881-b84e-4d3e-92eb-a0be333a6a0f" />

**Question 3**
---

<img width="1200" height="707" alt="image" src="https://github.com/user-attachments/assets/d20cb725-2645-4f63-9ce0-73eecc356267" />


```sql
select p.first_name as patient_name from patients p
join doctors d 
on p.doctor_id = d.doctor_id
where d.first_name='Emily' and d.last_name='Johnson' and p.discharge_date is not null;
```

**Output:**

<img width="1203" height="520" alt="image" src="https://github.com/user-attachments/assets/4a439e6a-6664-4b54-b910-946a8e544ea1" />

**Question 4**
---

<img width="1201" height="717" alt="image" src="https://github.com/user-attachments/assets/a50e34dc-6dbb-4e5a-8968-380797c21a4a" />


```sql
select p.* from patients p
join appointments a
on p.patient_id=a.patient_id
where a.appointment_date between '2024-01-01' and '2024-01-31';
```

**Output:**

<img width="1199" height="534" alt="image" src="https://github.com/user-attachments/assets/829193e7-bafe-457c-9a71-9f07ed7873ff" />

**Question 5**
---

<img width="1206" height="798" alt="image" src="https://github.com/user-attachments/assets/3ae20bd0-8b24-42ac-a3b0-7fa2a2c88874" />


```sql
select o.ord_no, o.purch_amt , c.cust_name, c.city from orders o
join customer c
on o.customer_id=c.customer_id
where o.purch_amt between 500 and 2000;
```

**Output:**

<img width="1198" height="595" alt="image" src="https://github.com/user-attachments/assets/85e1f711-8389-40a5-a5b9-cbea5d517e28" />

**Question 6**
---

<img width="1208" height="751" alt="image" src="https://github.com/user-attachments/assets/7289ec8a-9442-4fa1-8538-82b5aade0b4e" />


```sql
select n.*, d.department_name from nurses n
join departments d
on n.department_id=d.department_id;
```

**Output:**

<img width="1194" height="695" alt="image" src="https://github.com/user-attachments/assets/b4c507d9-ec4f-47e7-a85b-a8fbf5c51aaa" />

**Question 7**
---

<img width="1185" height="659" alt="image" src="https://github.com/user-attachments/assets/b212759a-3056-4f4c-9b03-6d43848b37e5" />


```sql
select p.* from patients p
join doctors d
on p.doctor_id=d.doctor_id
where d.first_name='John' and d.last_name='Smith';
```


**Output:**

<img width="1200" height="540" alt="image" src="https://github.com/user-attachments/assets/5fb1b8db-f4fc-476d-8e76-4b85b860b08c" />

**Question 8**
---

<img width="1194" height="680" alt="image" src="https://github.com/user-attachments/assets/1c77494c-a31e-4e39-af8f-aec0c3f26c07" />


```sql
select p.first_name, s.* from patients p
join surgeries s
on p.patient_id=s.patient_id
where p.discharge_date between '2024-03-01' and '2024-03-31' and not p.admission_date = p.discharge_date;
```

**Output:**

<img width="1205" height="537" alt="image" src="https://github.com/user-attachments/assets/1068910f-4fa0-4539-b660-97a1369a88a7" />

**Question 9**
---

<img width="1196" height="490" alt="image" src="https://github.com/user-attachments/assets/6fc18d79-095b-4ea2-920d-5f2bd9c49b53" />

```sql
select c.cust_name, o.ord_no, o.ord_date, o.purch_amt from customer c
left join orders o
on c.customer_id = o.customer_id;
```

**Output:**

<img width="1210" height="470" alt="image" src="https://github.com/user-attachments/assets/7fde6b81-820d-4d32-be82-765c6ce591bf" />

**Question 10**
---

<img width="1206" height="728" alt="image" src="https://github.com/user-attachments/assets/664f27a6-9781-4c94-bfa5-42c89b4961d3" />


```sql
select n.nurse_id, d.department_name from nurses n
join departments d
on n.department_id = d.department_id
where n.first_name='David' and n.last_name='Moore';
```

**Output:**

<img width="1200" height="526" alt="image" src="https://github.com/user-attachments/assets/60c17684-87bd-4199-9fa2-c0f049dd8851" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
