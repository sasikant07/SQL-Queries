## 1. Write a query to find the first_name, last_name and salaries of the employees who have a higher salary than the employee whose last_name is Bull.
`select first_name, last_name, salary from employees where salary > (select salary from employees where last_name = 'Bull');`

## 2. Write a SQL subquery to find the first_name and last_name of all employees who works in the IT department.
`select first_name, last_name from employees where department_id in(select department_id from departments where department_name = 'IT');`

## 3. Write a SQL subquery to find the first_name and last_name of the employees under a manager who works for a department based in the United States.
`select first_name, last_name from employees where manager_id in(select employee_id from employees where department_id in (select department_id from departments where location_id in(select location_id from locations where country_id = 'US')));`

## 4. Write a SQL subquery to find the first_name and last_name of the employees who are working as a manager.
`select first_name, last_name from employees where employee_id in(select manager_id from employees);`

## 5. Write a SQL subquery to find the first_name, last_name and salary, which is greater than the average salary of the employees.
`5. Write a SQL subquery to find the first_name, last_name and salary, which is greater than the average salary of the employees.`

## 6. Write a SQL subquery to find the first_name, last_name and salary, which is equal to the minimum salary for this post, he/she is working on.
`select first_name, last_name, salary from employees where employees.salary = (select min_salary from jobs where employees.job_id = jobs.job_id);`

## 7. Write a SQL Subquery to find the first_name, last_name and salary of the employees who earn more than the average salary and works in any of the IT departments.
`select first_name, last_name, salary from employees where department_id in(select department_id from departments where department_name LIKE 'IT%') and salary >(select avg(salary) from employees);`

## 8. Write a SQL subquery to find the first_name, last_name and salary of the employees who draw a more salary than the employee, which the last name is Bell.
`select first_name, last_name, salary from employees where salary > (select salary from employees where last_name = 'Bell') order by first_name;`

## 9. Write a SQL subquery to find all the information of the employees who draws the same salary as the minimum salary for all departments.
`select * from employees where salary = (select min(salary) from employees);`

## 10. Write a SQL subquery to find all the information of the employees whose salary greater than the average salary of all departments.
`select * from employees where salary > ALL(select AVG(salary) from employees group by department_id);`

## 11. Write a subquery to find the first_name, last_name, job_id and salary of the employees who draws a salary that is higher than the salary of all the Shipping Clerk (JOB_ID = 'SH_CLERK'). Sort the results on salary from the lowest to highest.
`select first_name, last_name, salary, job_id from employees where salary > ALL(select salary from employees where job_id = 'SH_CLERK') order by salary;`

## 12. Write a SQL subquery to find the first_name and last_name of the employees who are not supervisors.
`select b.first_name, b.last_name from employees b where NOT EXISTS (SELECT 'X' from employees a where a.manager_id = b.employee_id);`

## 13. Write a SQL subquery to find the employee ID, first name, last name and department names of all employees.
`select employee_id, first_name, last_name, (select department_name from departments d where e.department_id = d.department_id) AS Department from employees e order by Department;`

## 14. Write a SQL subquery to find the employee ID, first name, last name and salary of all employees whose salary is above the average salary for their departments.
`select employee_id, first_name from employees A where salary > (select AVG(salary) from employees where department_id = A.department_id);`

## 15. Write a subquery to find the 5th maximum salary of all salaries.
`select distinct salary from employees e1 where 5 = (select count(distinct salary) from employees e2 where e1.salary <= e2.salary);`

## 16. Write a subquery to find the 4th minimum salary of all the salaries.
`select distinct salary from employees e1 where 4 = (select count(distinct salary) from employees e2 where e1.salary >= e2.salary);`

## 17. Write a subquery to select last 10 records from a table.
`select * from (select * from employees order by employee_id desc limit 10) sub order by employee_id asc;`

## 18. Write a subquery to display the information for all the departments where no employee is working.
`select * from departments where department_id not in (select department_id from employees);`

## 19. Write a query to get three maximum salaries.
`select distinct salary from employees a where 3 >= (select count(distinct salary) from employees b where a.salary <= b.salary) order by salary desc;`

## 20. Write a query to get three minimum salaries.
`select distinct salary from employees a where 3 >= (select count(distinct salary) from employees b where a.salary >= b.salary) order by salary desc;`

## 21. Write a query to get nth max salaries of employees.
`select * from employees a where (1) = (select count(distinct(b.salary)) from employees b where b.salary > a.salary);`
