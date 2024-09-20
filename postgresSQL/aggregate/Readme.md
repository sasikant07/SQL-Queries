## 1. Write a query to find the number of jobs available in the employees table.
`select count(distinct job_id) from employees;`

## 2. Write a query to get the total salaries payable to employees.
`select sum(salary) from employees;`

## 3. Write a query to get the minimum salary from employees table.
`select min(salary) from employees;`

## 4. Write a query to get the maximum salary of an employee working as a Programmer.
`select max(salary) from employees where job_id = 'IT_PROG';`

## 5. Write a query to get the average salary and number of employees working in the department which ID is 90.
`select avg(salary), count(*) from employees where department_id = 90;`

## 6. Write a query to get the highest, lowest, total, and average salary of all employees.
`SELECT ROUND(MAX(salary),0) "Maximum", ROUND(MIN(salary),0) "Minimum", ROUND(SUM(salary),0) "Sum", ROUND(AVG(salary),0) "Average" FROM employees;`

## 7. Write a query to get the number of employees working in each post
`select job_id, count(*) from employees group by job_id;`

## 8. Write a query to get the difference between the highest and lowest salaries.
`SELECT MAX(salary) - MIN(salary) DIFFERENCE from employees;`

## 9. Write a query to find the manager ID and the salary of the lowest-paid employee under that manager.
`select manager_id, min(salary) from employees where manager_id is not null group by manager_id order by min(salary) desc;`

## 10. Write a query to get the department ID and the total salary payable in each department.
`select department_id, sum(salary) from employees group by department_id;`

## 11. Write a query to get the average salary for each post excluding programmer.
`select job_id, avg(salary) from employees where job_id <> 'IT_PROG' group by job_id;`

## 12. Write a query to get the total salary, maximum, minimum and average salary of all posts for those departments which ID 90.
`select job_id, AVG(salary), SUM(salary), MAX(salary), MIN(salary) from employees where department_id = '90' group by job_id;`

## 13. Write a query to get the job ID and maximum salary of each post for maximum salary is at or above $4000.
`select job_id, MAX(salary) from employees group by job_id having MAX(salary) >= 4000;`

## 14. Write a query to get the average salary for all departments working more than 10 employees.
`select department_id, AVG(salary), count(*) from employees group by department_id having count(*) > 10;`