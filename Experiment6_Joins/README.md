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
Write the SQL query that achieves the selection of all columns from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers with the name 'Fabian Johns'.

Answer: SELECT s.* FROM salesman s LEFT JOIN customer c ON s.salesman_id = c.salesman_id WHERE c.cust_name = 'Fabian Johns';
**Output:**
<img width="728" height="444" alt="image" src="https://github.com/user-attachments/assets/04252ee9-bd3d-4e83-b6ef-2384a2327b23" />


**Question 2**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission. Sample table: customer
<img width="724" height="343" alt="image" src="https://github.com/user-attachments/assets/e1336d36-0b26-4b0c-aa4c-c88dedd3433e" />

Sample table: salesman

<img width="579" height="320" alt="image" src="https://github.com/user-attachments/assets/6e847158-350d-463b-bfda-6cb12a03128c" />


Answer:

SELECT c.cust_name AS "Customer Name", c.city AS "city", s.name AS "Salesman", s.city AS "city", s.commission FROM customer c JOIN salesman s ON c.salesman_id = s.salesman_id WHERE c.city <> s.city AND s.commission > 0.12;


**Output:**
<img width="669" height="570" alt="image" src="https://github.com/user-attachments/assets/8ceee920-77ac-48c2-ade6-186dd61ea95e" />


**Question 3**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.

Answer: SELECT c.cust_name, o.ord_no, o.ord_date, o.purch_amt FROM customer c LEFT JOIN orders o ON c.customer_id = o.customer_id;

**Output:**
<img width="818" height="744" alt="image" src="https://github.com/user-attachments/assets/7201f238-1d09-4279-83f1-9e6567a38de6" />


**Question 4**
---
Write the SQL query that accomplishes the selection of all columns from the "patients" table and the first name of doctors from the "doctors" table, with an inner join on the "doctor_id" column. PATIENTS TABLE:

<img width="453" height="304" alt="image" src="https://github.com/user-attachments/assets/e8a2224d-eac3-491a-bcae-fa8673d8ec32" />
DOCTORS TABLE:
<img width="405" height="209" alt="image" src="https://github.com/user-attachments/assets/08ad1fcc-3467-4692-b71a-25d1ed9add2f" />

Answer: SELECT p.patient_id, p.first_name AS first_name, p.last_name AS last_name, p.date_of_birth, p.admission_date, p.discharge_date, p.doctor_id, d.first_name AS doctor_name FROM patients p INNER JOIN doctors d ON p.doctor_id = d.doctor_id;

**Output:**

<img width="721" height="571" alt="image" src="https://github.com/user-attachments/assets/ffcb89cf-19ce-408c-a966-34efe48e2008" />


**Question 5**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id. Sample table: customer

<img width="763" height="336" alt="image" src="https://github.com/user-attachments/assets/a8bcb671-9016-406b-9f35-8207b5b5b697" />

Sample table: salesman
<img width="697" height="278" alt="image" src="https://github.com/user-attachments/assets/90a992b8-fee7-4532-88c0-803c604bbdd9" />
Answer:

SELECT c.cust_name, c.city AS city, c.grade, s.name AS Salesman, s.city AS city FROM customer c JOIN salesman s ON c.salesman_id = s.salesman_id ORDER BY c.customer_id ASC;


**Output:**
<img width="855" height="505" alt="image" src="https://github.com/user-attachments/assets/35ab383d-bfd7-4530-af63-2df0a79c67b8" />


**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column. PATIENTS TABLE:

<img width="379" height="298" alt="image" src="https://github.com/user-attachments/assets/cd73a478-3a21-45a4-bebd-60e1d59dd41f" />

DOCTORS TABLE:
<img width="476" height="219" alt="image" src="https://github.com/user-attachments/assets/399e3041-cf89-4224-aa04-6d3981c7a6d7" />

Answer:

SELECT p.*, d.specialization AS doctor_specialization FROM patients p INNER JOIN doctors d ON p.doctor_id = d.doctor_id;



**Output:**
<img width="661" height="492" alt="image" src="https://github.com/user-attachments/assets/35b1c3ad-ca7d-4def-9882-530841d61d2f" />


**Question 7**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. Sample table: customer

<img width="825" height="339" alt="image" src="https://github.com/user-attachments/assets/f631a548-31a3-4f68-84af-574767b2f0aa" />
Sample table: salesman
<img width="595" height="308" alt="image" src="https://github.com/user-attachments/assets/ace7f34d-daa8-4a49-8bec-22a5b56b513d" />

Answer:

SELECT c.cust_name, c.city AS city, c.grade, s.name AS Salesman, s.city AS city FROM customer c INNER JOIN salesman s ON c.salesman_id = s.salesman_id WHERE c.grade < 300 ORDER BY c.customer_id ASC;

**Output:**
<img width="853" height="479" alt="image" src="https://github.com/user-attachments/assets/bdec9979-e07f-40a4-9ede-d36425eb9a07" />


**Question 8**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city. Sample table: salesman
<img width="637" height="264" alt="image" src="https://github.com/user-attachments/assets/8acbc41f-a1a0-48b2-ac3d-e8eb36564b1d" />
Sample table: customer
<img width="803" height="340" alt="image" src="https://github.com/user-attachments/assets/e53fc587-0b00-477c-82c8-4dab5358b428" />

Answer:

SELECT s.name AS Salesman, c.cust_name, s.city FROM salesman s INNER JOIN customer c ON s.city = c.city;

**Output:**
<img width="867" height="563" alt="image" src="https://github.com/user-attachments/assets/7b4246b8-bd9a-4125-8e6f-e5d62b228139" />


**Question 9**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:

<img width="431" height="282" alt="image" src="https://github.com/user-attachments/assets/d54463b2-2d5d-41f1-8e6e-331f6a365541" />

SURGERIES TABLE:
<img width="341" height="205" alt="image" src="https://github.com/user-attachments/assets/ca15506a-a473-4fa9-860d-397052dadd36" />

Answer:

SELECT p.first_name, s.surgery_id, s.patient_id, s.surgeon_id, s.surgery_date FROM patients p INNER JOIN surgeries s ON p.patient_id = s.patient_id WHERE p.first_name = 'Alice';


**Output:**

<img width="553" height="319" alt="image" src="https://github.com/user-attachments/assets/91921498-af5e-4fab-9e9e-da6deed28ff5" />


**Question 10**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. Sample table: orders image

<img width="672" height="450" alt="image" src="https://github.com/user-attachments/assets/f24aae8f-3ec1-4183-9117-181716185f14" />

Sample table: customer image
<img width="790" height="326" alt="image" src="https://github.com/user-attachments/assets/e05ee323-5e5d-43b6-9abf-b459919bc8c3" />

Sample table : salesman image
<img width="621" height="262" alt="image" src="https://github.com/user-attachments/assets/f2e77a7a-5c1a-47f6-ba6e-b7a34eace1fd" />

Answer:

SELECT o.ord_no, o.purch_amt, o.ord_date, c.cust_name, c.city AS customer_city, c.grade, s.name AS salesman_name, s.city AS salesman_city, s.commission FROM orders o INNER JOIN customer c ON o.customer_id = c.customer_id INNER JOIN salesman s ON o.salesman_id = s.salesman_id;

**Output:**
<img width="865" height="464" alt="image" src="https://github.com/user-attachments/assets/759d40b9-6b5e-46fd-8cf8-ca378b599f5c" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
