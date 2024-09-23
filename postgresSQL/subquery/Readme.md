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

