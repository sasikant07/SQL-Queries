## 1. Write a query to display the names (first_name, last_name) using an alias name "First Name", "Last Name"
`SELECT FIRST_NAME "First Name", LAST_NAME "Last Name" from employees;`

## 2. Write a query to get a unique department ID from employee table.
`select distinct department_id from employees;`

## 3. Write a query to get the details of all employees from the employee table in descending order by their first name.
`select * from employees order by first_name desc;`

## 4. Write a query to get the names (first_name, last_name), salary and 15% of salary as PF for all the employees
`select first_name, last_name, salary, salary * 0.15 PF from employees;`

## 5. Write a query to get the employee ID, name (first_name, last_name) and salary in ascending order according to their salary.
`select employee_id, first_name, last_name, salary from employees order by salary;`

## 6. Write a query to get the total salaries payable to employees.
`select SUM(salary) from employees;`

## 7. Write a query to get the maximum and minimum salary paid to the employees
`select max(salary), min(salary) from employees;`

## 8. Write a query to get the average salary and number of employees are working.
`select avg(salary), count(*) from employees;`

## 9. Write a query to get the number of employees working with the company.
`select count(*) from employees;`

## 10. Write a query to get the unique number of designations available in the employees table.
`select count(distinct job_id) from employees;`

## 11. Write a query to get all the first name from the employees table in upper case.
`select UPPER(first_name) from employees;`