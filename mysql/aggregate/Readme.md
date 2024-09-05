## 1. Write a query to list the number of jobs available in the employees table.
`Write a query to list the number of jobs available in the employees table.`

## 2. Write a query to get the total salaries payable to employees.
`SELECT SUM(SALARY) from Employees;`

## 3. Write a query to get the minimum salary from employees table.
`SELECT MIN(SALARY) from Employees;`

## 4. Write a query to get the maximum salary of an employee working as a Programmer.
`SELECT MAX(SALARY) from Employees where JOB_ID="IT_PROG";`

## 5. Write a query to get the average salary and number of employees working the department 90
`SELECT AVG(SALARY), COUNT(*) from Employees where DEPARTMENT_ID="90";`

## 6. Write a query to get the highest, lowest, sum, and average salary of all employees.
`SELECT ROUND(MAX(SALARY), 0) "Maximum", ROUND(MIN(SALARY), 0) "Minimum",ROUND(SUM(SALARY), 0) "Total", ROUND(AVG(SALARY), 0) "Average" from Employees;`

## 7. Write a query to get the number of employees with the same job.
`SELECT JOB_ID, COUNT(*) from Employees GROUP BY JOB_ID;`

## 8. Write a query to get the difference between the highest and lowest salaries.
`SELECT MAX(SALARY) - MIN(SALARY) DIFFERENCE from Employees;`

## 9. Write a query to find the manager ID and the salary of the lowest-paid employee for that manager.
`SELECT MANAGER_ID, MIN(SALARY) from Employees where MANAGER_ID IS NOT NULL GROUP BY MANAGER_ID ORDER BY MIN(SALARY) DESC;`