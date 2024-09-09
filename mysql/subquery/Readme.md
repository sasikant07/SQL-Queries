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

## 8. Write a MySQL query to find the name (first_name, last_name), and salary of the employees who earns more than the employee whose last name is Bell.

`select FIRST_NAME, LAST_NAME, SALARY from employees where SALARY > (select SALARY from employees where LAST_NAME = "Bell") order by FIRST_NAME;`

## 9. Write a MySQL query to find the name (first_name, last_name), and salary of the employees who earn the same salary as the minimum salary for all departments.

`select * from employees where SALARY = (select min(SALARY) from employees);`

## 10. Write a MySQL query to find the name (first_name, last_name), and salary of the employees whose salary is greater than the average salary of each department.

`select * from employees where SALARY > all (select avg(SALARY) from employees group by DEPARTMENT_ID);`

## 11. Write a MySQL query to find the name (first_name, last_name) and salary of the employees who earn a salary that is higher than the salary of all the Shipping Clerk (JOB_ID = 'SH_CLERK'). Sort the results of the salary of the lowest to highest.

`select FIRST_NAME, LAST_NAME, JOB_ID, SALARY from employees where SALARY > all (select SALARY from employees where JOB_ID = 'SH_CLERK') ORDER BY SALARY;`

## 12. Write a MySQL query to find the name (first_name, last_name) of the employees who are not supervisors.

`select b.FIRST_NAME, b.LAST_NAME from employees b where not exists (select "X" from employees a where a.MANAGER_ID = b.EMPLOYEE_ID);`

## 13. Write a MySQL query to display the employee ID, first name, last name, and department names of all employees.

`select EMPLOYEE_ID, FIRST_NAME, LAST_NAME, (select DEPARTMENT_NAME from departments d where e.DEPARTMENT_ID = d.DEPARTMENT_ID) department from employees e ORDER BY department;`

## 14. Write a MySQL query to display the employee ID, first name, last name, salary of all employees whose salary is above average for their departments.

`select EMPLOYEE_ID, FIRST_NAME, LAST_NAME, SALARY from employees A where SALARY > (select avg(SALARY) from employees where DEPARTMENT_ID = A.DEPARTMENT_ID);`
