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

## 10. Write a query to get the department ID and the total salary payable in each department
`SELECT DEPARTMENT_ID, SUM(SALARY) AS TOTAL_SALARY from Employees group by DEPARTMENT_ID;`

## 11. Write a query to get the average salary for each job ID excluding programmer.
`SELECT JOB_ID, AVG(SALARY) from Employees where JOB_ID <> "DEV" group by JOB_ID;`

## 12. Write a query to get the total salary, maximum, minimum, average salary of employees (job ID wise), for department ID 90 only.
`SELECT JOB_ID, SUM(SALARY) AS TOTAL_SALARY, MAX(SALARY) AS MAX, MIN(SALARY) AS MIN, AVG(SALARY) AS AVG_SALARY from Employees where DEPARTMENT_ID = "3" group by JOB_ID;`

## 13. Write a query to get the job ID and maximum salary of the employees where maximum salary is greater than or equal to $4000.
`SELECT JOB_ID, MAX(SALARY) from Employees group by JOB_ID having MAX(SALARY) >= 4000;`

## 14. Write a query to get the average salary for all departments employing more than 10 employees.
`SELECT DEPARTMENT_ID, max(SALARY), count(*) from Employees group by DEPARTMENT_ID having count(*) > 10;`