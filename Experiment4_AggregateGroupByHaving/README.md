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

<img width="1200" height="571" alt="image" src="https://github.com/user-attachments/assets/84fa19c6-0af0-4923-9e96-94729cf48d8e" />


```sql
select avg(purch_amt) as AVERAGE from orders;
```

**Output:**

<img width="1202" height="435" alt="image" src="https://github.com/user-attachments/assets/eae9f53a-f625-4edb-aca0-0fc2333a4724" />

**Question 2**
---

<img width="1195" height="547" alt="image" src="https://github.com/user-attachments/assets/38eb2a61-e8c5-4dbb-878c-1f1e556e102f" />

```sql
select (max(price)-min(price)) as price_diff from fruits;
```

**Output:**

<img width="1199" height="423" alt="image" src="https://github.com/user-attachments/assets/a8b74089-7364-4948-9394-761231fe18c5" />

**Question 3**
---

<img width="1191" height="521" alt="image" src="https://github.com/user-attachments/assets/0848656f-5c09-4af9-ad67-2e34dfed98ec" />


```sql
select avg(length(email)) as avg_email_length_below_30 from customer
where city in ('Mumbai');
```

**Output:**

<img width="1197" height="428" alt="image" src="https://github.com/user-attachments/assets/b1316147-211d-48ad-ba7c-0eb1702172ad" />

**Question 4**
---

<img width="1204" height="728" alt="image" src="https://github.com/user-attachments/assets/5d9c0658-800a-4535-be15-078c679a7699" />

```sql
select InsuranceCompany, count(*) as TotalExpiredPatients from Insurance
group by InsuranceCompany;

```

**Output:**

<img width="1203" height="799" alt="image" src="https://github.com/user-attachments/assets/2cbe5b86-20c3-4bb1-b3d1-1932be8d53ff" />

**Question 5**
---

<img width="1197" height="647" alt="image" src="https://github.com/user-attachments/assets/38b76945-5ee0-4b66-be0e-4fb0990e7081" />


```sql
select strftime("%Y",ValidityPeriod) as ValidityYear, count(*) as TotalPatients from Insurance
group by strftime("%Y",ValidityPeriod);
```

**Output:**

<img width="1199" height="510" alt="image" src="https://github.com/user-attachments/assets/a2b73c8c-8b21-4447-b3b6-9bb63873a9e1" />

**Question 6**
---

<img width="1202" height="658" alt="image" src="https://github.com/user-attachments/assets/a0114dd7-3c4a-4cf4-9329-7569c5b3350f" />

```sql
select PatientID, count(*) as TotalAppointments from Appointments
group by PatientID;
```

**Output:**

<img width="1202" height="755" alt="image" src="https://github.com/user-attachments/assets/d3856fab-d247-439c-b036-3b1c9edbdf0b" />

**Question 7**
---

<img width="1203" height="602" alt="image" src="https://github.com/user-attachments/assets/ac6bd411-e6cc-4ca1-84eb-71223111534d" />


```sql
SELECT age, min(Income) as Income from employee
group by age
having min(Income)<1000000;
```

**Output:**

<img width="1202" height="561" alt="image" src="https://github.com/user-attachments/assets/8c9a85b4-f444-4094-80a8-7a52655104e7" />

**Question 8**
---

<img width="1202" height="547" alt="image" src="https://github.com/user-attachments/assets/011daffa-23a5-41b9-9893-19a453273ee1" />


```sql
select age, MAX(income) from employee
group by age
having max(income)>2000000;
```

**Output:**

<img width="1201" height="477" alt="image" src="https://github.com/user-attachments/assets/f163e7ff-6591-483d-8d12-b5caf53f341c" />

**Question 9**
---

<img width="1202" height="611" alt="image" src="https://github.com/user-attachments/assets/1ed39449-b6f6-49f0-9de5-3b91e2cc2e08" />


```sql
select occupation , MIN(workhour) from employee1
group by occupation
having min(workhour)>8;
```

**Output:**

<img width="1195" height="609" alt="image" src="https://github.com/user-attachments/assets/9f7b7adf-23c6-4878-843f-10bf97bbc1c0" />

**Question 10**
---

<img width="1197" height="588" alt="image" src="https://github.com/user-attachments/assets/ed61cd89-9063-4f95-9462-1bb0f6e65d72" />


```sql
select city, AVG(income) from employee
group by city
having avg(income)>500000;
```

**Output:**

<img width="1198" height="557" alt="image" src="https://github.com/user-attachments/assets/330a9445-cc4b-4148-85eb-c9dae2029336" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
