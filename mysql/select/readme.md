# Employees Table
`
CREATE TABLE Employees (
    EMPLOYEE_ID INT AUTO_INCREMENT PRIMARY KEY,
    FIRST_NAME VARCHAR(50),
    LAST_NAME VARCHAR(50),
    EMAIL VARCHAR(100),
    PHONE_NUMBER VARCHAR(20),
    HIRE_DATE DATE,
    JOB_ID VARCHAR(10),
    SALARY DECIMAL(10, 2),
    COMMISSION_PCT DECIMAL(5, 2),
    MANAGER_ID INT,
    DEPARTMENT_ID INT
);
`
`
INSERT INTO Employees (FIRST_NAME, LAST_NAME, EMAIL, PHONE_NUMBER, HIRE_DATE, JOB_ID, SALARY, COMMISSION_PCT, MANAGER_ID, DEPARTMENT_ID) VALUES
('John', 'Doe', 'john.doe@example.com', '555-0100', '2020-01-15', 'DEV', 60000.00, 0.05, NULL, 1),
('Jane', 'Smith', 'jane.smith@example.com', '555-0101', '2021-02-20', 'DEV', 62000.00, 0.07, 1, 2),
('Emily', 'Jones', 'emily.jones@example.com', '555-0102', '2019-03-25', 'HR', 55000.00, 0.10, NULL, 1),
('Michael', 'Brown', 'michael.brown@example.com', '555-0103', '2018-04-30', 'DEV', 65000.00, 0.08, 1, 1),
('Sara', 'Johnson', 'sara.johnson@example.com', '555-0104', '2022-05-15', 'MGR', 70000.00, NULL, NULL, 2),
('David', 'Williams', 'david.williams@example.com', '555-0105', '2017-06-10', 'DEV', 72000.00, 0.09, 5, 3),
('Laura', 'Garcia', 'laura.garcia@example.com', '555-0106', '2021-07-05', 'HR', 58000.00, 0.12, 5, 2),
('Chris', 'Martinez', 'chris.martinez@example.com', '555-0107', '2016-08-20', 'DEV', 63000.00, 0.06, 7, 3),
('Nancy', 'Wilson', 'nancy.wilson@example.com', '555-0108', '2023-09-15', 'MGR', 71000.00, NULL, NULL, 3),
('James', 'Anderson', 'james.anderson@example.com', '555-0109', '2022-10-30', 'DEV', 64000.00, 0.05, 9, 1),
('Karen', 'Thomas', 'karen.thomas@example.com', '555-0110', '2024-11-12', 'HR', 57000.00, 0.11, 8, 2),
('Robert', 'Taylor', 'robert.taylor@example.com', '555-0111', '2020-12-15', 'DEV', 66000.00, 0.07, 2, 1),
('Alice', 'Harris', 'alice.harris@example.com', '555-0112', '2019-01-05', 'HR', 54000.00, 0.09, 3, 2),
('Tom', 'Clark', 'tom.clark@example.com', '555-0113', '2018-03-10', 'DEV', 67000.00, 0.10, 6, 1),
('Megan', 'Lewis', 'megan.lewis@example.com', '555-0114', '2021-04-25', 'HR', 56000.00, 0.08, 7, 2),
('Paul', 'Walker', 'paul.walker@example.com', '555-0115', '2022-06-15', 'DEV', 69000.00, 0.06, 2, 1),
('Linda', 'Hall', 'linda.hall@example.com', '555-0116', '2020-08-20', 'HR', 55000.00, 0.07, 4, 2),
('Scott', 'Allen', 'scott.allen@example.com', '555-0117', '2019-09-30', 'DEV', 68000.00, 0.05, 5, 1),
('Olivia', 'Young', 'olivia.young@example.com', '555-0118', '2018-11-25', 'HR', 59000.00, 0.10, 6, 2),
('Jack', 'King', 'jack.king@example.com', '555-0119', '2021-01-10', 'DEV', 71000.00, 0.08, 7, 1),
('Sophia', 'Wright', 'sophia.wright@example.com', '555-0120', '2022-02-20', 'MGR', 73000.00, NULL, NULL, 1);

`


## 1. Write a query to display the names (first_name, last_name) using alias name "First Name", "Last Name".

`SELECT first_name "First Name" last_name "Last Name" from Employees;`

## 2. Write a query to get unique department ID from employee table.
`SELECT DISTINCT department_id FROM employees;`

Output:

+---------------+
| DEPARTMENT_ID |
+---------------+
|             1 |
|             2 |
|             3 |
+---------------+

## 3. Write a query to get the details of all employees according to first name in descending order.
`SELECT * from Employees ORDER BY FIRST_NAME DESC;`

## 4. Write a query to get the employee ID, name (first_name, last_name), salary in ascending order of salary.
`SELECT EMPLOYEE_ID, FIRST_NAME, LAST_NAME, SALARY FROM Employees ORDER BY SALARY;`

## 5. Write a query to get the names (first_name, last_name), salary, PF of all the employees (PF is calculated as 15% of salary).
`SELECT CONCAT(FIRST_NAME, ' ', LAST_NAME) AS Full_Name, SALARY * 0.15 AS PF from Employees;`

## 6. Write a query to get the total salaries payable to employees.
`SELECT SUM(SALARY) AS Total_Salries from Employees;`

## 7. Write a query to get the maximum and minimum salary from employees table.
`SELECT MAX(SALARY), MIN(SALARY) from Employees;`


## 8. Write a query to get the average salary and number of employees in the employees table.
`SELECT AVG(SALARY), count(*) from Employees;`

## 9. Write a query to get the number of employees working with the company.
`SELECT count(*) AS NUM_OF_EMPLOYEES from Employees;`

## 10. Write a query to get the number of designations available in the employees table.
`SELECT count(DISTINCT JOB_ID) from Employees;`

## 11. Write a query get all first name from employees table in upper case.
`SELECT UPPER(FIRST_NAME) from Employees;`