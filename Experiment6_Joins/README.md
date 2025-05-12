# Experiment 6: Joins
# Name: Mahalakshmi.R
# Reference Number: 212223230117
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
From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT c.cust_name AS "Customer Name",c.city,s.name AS "Salesman",s.commission FROM customer c JOIN salesman s ON c.salesman_id=s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/7d598420-c835-4698-81ca-de40d0fdcd1d)


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "patients" table, with an inner join on the "doctor_id" column, and includes a condition filtering for patients whose doctors have the first name 'John' and last name 'Smith'.

```sql
SELECT p.patient_id,p.first_name,p.last_name,p.date_of_birth,p.admission_date,p.discharge_date,d.doctor_id FROM PATIENTS p INNER JOIN DOCTORS d ON p.doctor_id=d.doctor_id WHERE d.first_name="John" AND d.last_name="Smith";
```

**Output:**
![image](https://github.com/user-attachments/assets/78fe21a4-27df-436c-a45b-34c6d7720ac7)


**Question 3**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

```sql
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt AS "Order Amount",s.name,s.commission FROM customer c 
LEFT JOIN orders o ON c.customer_id=o.customer_id
LEFT JOIN salesman s ON s.salesman_id=o.salesman_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/6f2e882d-a4c5-44d2-bb7c-5103db996d48)


**Question 4**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

```sql
SELECT c.cust_name,c.city,c.grade,s.name AS "Salesman",s.city FROM customer c 
LEFT JOIN salesman s ON s.salesman_id=c.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**
![image](https://github.com/user-attachments/assets/2610d0be-3718-4e8b-a1ad-1ba42350ec0a)


**Question 5**
---
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.

```sql
SELECT n.nurse_id,d.department_name FROM NURSES n
INNER JOIN DEPARTMENTS d ON n.department_id=d.department_id
WHERE n.last_name="Moore" AND n.first_name="David";
```

**Output:**
![image](https://github.com/user-attachments/assets/9be220f1-b473-4bab-846a-b57dcd30961d)


**Question 6**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for customers with a grade less than or equal to 100.

```sql
SELECT s.name,c.cust_name,c.city,c.grade,c.salesman_id FROM Customer c 
LEFT JOIN Salesman s ON s.salesman_id=c.salesman_id
WHERE grade<=100;
```

**Output:**
![image](https://github.com/user-attachments/assets/781ffd94-3590-4cf0-860c-15d4bd60cfa4)

**Question 7**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column.

```sql
SELECT s.name,c.cust_name,c.city,c.grade,c.salesman_id FROM salesman s 
LEFT JOIN customer c ON s.salesman_id=c.salesman_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/143f6f34-2558-4006-88f8-e6fd3a165b1c)


**Question 8**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission. 

```sql
SELECT c.cust_name AS "Customer Name",c.city,s.name AS "Salesman",s.commission FROM customer c
LEFT JOIN salesman s ON c.salesman_id=s.salesman_id
WHERE s.commission>.12;
```

**Output:**
![image](https://github.com/user-attachments/assets/6830df9e-f111-4fa3-aecc-805dea433862)


**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.

```sql
SELECT p.patient_id,p.first_name,p.last_name,p.date_of_birth,p.admission_date,p.discharge_date,p.doctor_id,d.specialization AS "doctor_specialization" FROM PATIENTS p
INNER JOIN DOCTORS d ON p.doctor_id=d.doctor_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/cf3e05a2-f8fd-4cb8-81e6-9c8286f53fc3)


**Question 10**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

```sql
SELECT s.name AS "Salesman",c.cust_name,c.city FROM salesman s
JOIN customer c ON c.city=s.city;
```

**Output:**

![image](https://github.com/user-attachments/assets/350f6951-3c6b-42e2-9a63-0420f9b064b0)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
