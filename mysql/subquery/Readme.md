## 1. Write a MySQL query to find the name (first_name, last_name) and the salary of the employees who have a higher salary than the employee whose last_name='Bull'.

`Select FIRST_NAME, LAST_NAME, SALARY from Employees where SALARY > (Select salary from Employees where LAST_NAME = "Bull");`

## 2. Write a MySQL query to find the name (first_name, last_name) of all employees who works in the IT department.

`SELECT FIRST_NAME, LAST_NAME from employees where DEPARTMENT_ID IN (SELECT DEPARTMENT_ID from departments where DEPARTMENT_NAME = "IT");`

## 3. Write a MySQL query to find the name (first_name, last_name) of the employees who have a manager and worked in a USA based department.

`select FIRST_NAME, LAST_NAME from employees where MANAGER_ID IN (select EMPLOYEE_ID from employees where DEPARTMENT_ID IN (select DEPARTMENT_ID from departments where LOCATION_ID IN (select LOCATION_ID from locations where country_id="US")));`

## 4. Write a MySQL query to find the name (first_name, last_name) of the employees who are managers.

`select FIRST_NAME, LAST_NAME from employees where EMPLOYEE_ID IN (select MANAGER_ID from employees);`

## 5. Write a MySQL query to find the name (first_name, last_name), and salary of the employees whose salary is greater than the average salary.

`select FIRST_NAME, LAST_NAME, SALARY from employees where SALARY > (select AVG(SALARY) from employees);`

## 6. Write a MySQL query to find the name (first_name, last_name), and salary of the employees whose salary is equal to the minimum salary for their job grade.

`select FIRST_NAME, LAST_NAME, SALARY from employees where employees.SALARY = (select MIN_SALARY from jobs where employees.JOB_ID = jobs.JOB_ID);`

## 7. Write a MySQL query to find the name (first_name, last_name), and salary of the employees who earns more than the average salary and works in any of the IT departments.

`select FIRST_NAME, LAST_NAME, SALARY from employees where DEPARTMENT_ID IN (select DEPARTMENT_ID from departments where DEPARTMENT_NAME LIKE "IT%") AND SALARY > (select AVG(SALARY) from employees);`
