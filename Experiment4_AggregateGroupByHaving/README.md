## Experiment 4: Aggregate Functions, Group By and Having Clause

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
Sample table:Appointments Table
<img width="427" height="273" alt="image" src="https://github.com/user-attachments/assets/c592868c-a925-4603-945f-74ec6cf35eb4" />

Answer: SELECT strftime('%H',AppointmentDateTime) AS HourOfDay, COUNT(*) AS TotalAppointments FROM Appointments GROUP BY strftime('%H',AppointmentDateTime) ORDER BY HourOfDay;

**Output:**
<img width="850" height="686" alt="image" src="https://github.com/user-attachments/assets/ceb9ded8-9cf2-4fb9-a6b2-5fdebb16b5f5" />


**Question 2**
---
How many patients are there in each age group category (e.g., under 20, 20-30, 30-40, etc.)? Sample table: Patients Table

Answer:
<img width="867" height="649" alt="image" src="https://github.com/user-attachments/assets/f16d31e7-1630-49b4-8eb0-2a69f3f86493" />



**Output:**

<img width="587" height="402" alt="image" src="https://github.com/user-attachments/assets/895c0309-aac4-45a0-ace2-bc12de287947" />


**Question 3**
---
-How many prescriptions were written in each frequency category (e.g., once daily, twice daily)? Sample tablePrescriptions Table

Answer: SELECT Frequency, COUNT(*) AS TotalPrescriptions FROM Prescriptions GROUP BY Frequency ORDER BY Frequency;


**Output:**
<img width="814" height="617" alt="image" src="https://github.com/user-attachments/assets/cec39762-9e8e-4cf1-ac6d-bb2e7dc651ba" />


**Question 4**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': Table: employee

<img width="278" height="235" alt="image" src="https://github.com/user-attachments/assets/bd81a468-6a6d-4201-8199-f2e019ddb9c9" />

Answer: SELECT AVG(income) AS avg_income FROM employee WHERE name LIKE 'A%'; 
**Output:**
<img width="468" height="305" alt="image" src="https://github.com/user-attachments/assets/a08f5b12-bdd0-46a9-b553-d272208b2b35" />

**Question 5**
Write a SQL query to calculate the total number of working hours of all employees Sample table: employee1

Answer:

SELECT SUM(workhour) AS "Total working hours" FROM employee1;



**Output:**

<img width="671" height="375" alt="image" src="https://github.com/user-attachments/assets/9bdb63e5-2ed2-4e16-96a2-928fa0d706f1" />


**Question 6**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.
<img width="664" height="164" alt="image" src="https://github.com/user-attachments/assets/ea0a1e90-8713-4961-8ac4-86d5beb0eeca" />

Answer: SELECT SUM(purch_amt) AS TOTAL FROM orders;

**Output:**
<img width="632" height="427" alt="image" src="https://github.com/user-attachments/assets/d135bcb2-fff0-4b56-8ac8-79609defcb75" />

**Question 7**
Write a SQL query to count the number of customers. Return number of customers. Sample table: customer

<img width="727" height="162" alt="image" src="https://github.com/user-attachments/assets/7929c22d-2243-4f9d-9e55-62124957d86d" />

Answer:

SELECT COUNT(cust_name) AS COUNT FROM customer;

**Output:**
<img width="531" height="371" alt="image" src="https://github.com/user-attachments/assets/5279c865-ac80-4cf5-86a3-c2094eab37cf" />


**Question 8**
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

Answer:

SELECT jdate,MIN(workhour) AS "MIN(workhour)" FROM employee1 GROUP BY jdate HAVING MIN(workhour)<10;


**Output:**

<img width="753" height="512" alt="image" src="https://github.com/user-attachments/assets/6ff5a142-2f70-4018-a02e-3f2172f036ca" />


**Question 9**
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Answer:

SELECT (age -(age%5)) AS age_group, AVG(age) AS "AVG(age)" FROM customer1 GROUP BY age_group HAVING AVG(age)<=24;

**Output:**

<img width="718" height="364" alt="image" src="https://github.com/user-attachments/assets/4119e8b0-24b9-462a-8795-f602015895ef" />


**Question 10**
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Answer:

SELECT occupation, MIN(workhour) AS "MIN(workhour)" FROM employee1 group by occupation having min(workhour)>8; 
**Output:**

<img width="853" height="649" alt="image" src="https://github.com/user-attachments/assets/6ea04f83-18e0-461e-8e65-68cec87f2cc6" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
