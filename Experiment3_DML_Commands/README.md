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
Write a query to fetch 3 top salaried records from the EmployeePosition table. EmpID EmpPosition DateOfJoining Salary 1 Manager 01/05/2024 500000 2 Executive 02/05/2024 75000

**Answer:**
```
SELECT EmpID,EmpPosition,DateOfJoining,Salary
FROM EmployeePosition ORDER BY Salary DESC LIMIT 3;
```

**Output:**
<img width="856" height="190" alt="image" src="https://github.com/user-attachments/assets/07e3492d-cfd8-4255-a7a0-fdeca3af2b66" />


**Question 2**
Write a SQL query to Select all patients who were admitted for one day.

<img width="378" height="282" alt="image" src="https://github.com/user-attachments/assets/b3644206-d3a5-46f2-af9d-87056348eda4" />


**Answer:**
```
SELECT patient_id,first_name,admission_date,discharge_date FROM Patients WHERE admission_date==discharge_date;
```
**Output:**

<img width="860" height="241" alt="image" src="https://github.com/user-attachments/assets/21fdf6a7-9f78-4dae-b613-7ce0507a4e0f" />


**Question 3**
Write a SQL query to classify value2 in the Calculations table as 'Small', 'Medium', or 'Large' based on whether it is less than 10, between 10 and 50, or greater than 50, respectively.
<img width="726" height="293" alt="image" src="https://github.com/user-attachments/assets/e7f49303-1afb-4471-95bc-2b36e01d28d5" />


**Answer:**
```
SELECT id,value2,
CASE WHEN value2<10 THEN 'Small' WHEN value2 BETWEEN 10 AND 50 THEN 'Medium' ELSE 'Large' END AS size_category FROM Calculations;
```
 **Output:**

<img width="867" height="491" alt="image" src="https://github.com/user-attachments/assets/fa6f944e-11b6-4409-86d2-ab9e39fb03e2" />


**Question 4**
Write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id. Sample table: customer

<img width="719" height="179" alt="image" src="https://github.com/user-attachments/assets/c2ab9668-45b7-4c21-9d3e-2dd99cd2590d" />


**Answer:**
```
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer WHERE grade IS NULL;
```
**Output:**

<img width="860" height="286" alt="image" src="https://github.com/user-attachments/assets/ff9e6ae7-03f4-46dc-8bcc-76355783f98d" />


**Question 5**
Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id. Sample table: customer

<img width="731" height="176" alt="image" src="https://github.com/user-attachments/assets/8df2b3a4-f506-4a81-bc8e-76bd1af27d3a" />


**Answer:**
```
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer WHERE city = 'New York' OR grade <=100;
```
**Output:**

<img width="856" height="302" alt="image" src="https://github.com/user-attachments/assets/bbdab734-efe2-44bc-8337-63feae043e97" />


**Question 6**
Write a SQL query to identify products where the discount amount is greater than $50. Return product_id, original_price, discount_percentage, and discount_amount. Sample table: products
<img width="563" height="177" alt="image" src="https://github.com/user-attachments/assets/b4bfd173-d817-4765-a4f9-122de766288c" />

**Answer:**
```
SELECT product_id, original_price,discount_percentage,original_price * discount_percentage AS discount_amount
FROM products WHERE original_price * discount_percentage > 50;
```
**Output:**

<img width="862" height="224" alt="image" src="https://github.com/user-attachments/assets/c32b5e29-8d5e-47fa-adaf-da29c07a63da" />

**Question 7**
Write a SQL query to calculate the original price using the discount percentage and the given discounted price. Return product_id, discounted_price, discount_percentage, and original_price. Sample table: Products
<img width="588" height="181" alt="image" src="https://github.com/user-attachments/assets/a5e33298-307e-428d-8797-b647fc75dc80" />

**Answer:**
```
SELECT product_id,discounted_price,discount_percentage, discounted_price/(1 discount_percentage) AS original_price FROM Products;
```
 **Output:**

<img width="862" height="205" alt="image" src="https://github.com/user-attachments/assets/1705b9be-3442-4f20-b7f6-8af563b503ed" />


**Question 8**
Write a SQL query to find all employees along with the day of the week on which they were hired from the emp table emp table
<img width="434" height="346" alt="image" src="https://github.com/user-attachments/assets/bd011186-f922-4205-8587-82f4a42e66d7" />
**Answer:**
```
SELECT ename,hiredate, CASE strftime('%w',hiredate) WHEN '0' THEN 'Sunday' WHEN '1' THEN 'Monday' WHEN '2' THEN 'Tuesday' WHEN '3' THEN 'Wednesday' WHEN '4' THEN 'Thursday' WHEN '5' THEN 'Friday' WHEN '6' THEN 'Saturday' END AS day_of_week FROM emp;
```
**Output:**

<img width="855" height="571" alt="image" src="https://github.com/user-attachments/assets/19c779b4-2d35-4be5-9e28-9593b6a89591" />


**Question 9**
Write a SQL query to find all employees who were hired on a weekend (Saturday or Sunday) from the emp table emp table
<img width="507" height="351" alt="image" src="https://github.com/user-attachments/assets/0b7582f5-18ce-4277-8b03-62f2257db762" />


**Answer:**
```
SELECT ename,hiredate, CASE strftime('%w',hiredate) WHEN '0' THEN '0' WHEN '6' THEN '6' END AS day_of_week FROM emp WHERE strftime('%w',hiredate) IN ('0','6');
```
**Output:**
<img width="841" height="257" alt="image" src="https://github.com/user-attachments/assets/588c1f74-9827-40e2-a0ff-facd4ab5f928" />


**Question 10**
Write a SQL query to Concatenate the first three characters of the employee's name with the last three characters of their job title. Table name: emp

**Answer:**
```
SELECT ename,job,substr(ename,1,3) || substr(job,-3) AS ConcatenatedString FROM emp;
```
**Output:**

<img width="842" height="378" alt="image" src="https://github.com/user-attachments/assets/0b0f501b-c071-4f78-ac50-537658f4a752" />



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
