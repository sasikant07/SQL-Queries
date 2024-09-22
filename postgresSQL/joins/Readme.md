## 1. Write a query to find the addresses, including location_id, street_address, city, state_province and country_name of all the departments.
`select location_id, street_address, state_province, city, country_name, department_name from locations natural join countries natural join departments;`

## 2. Write a query to make a join with employees and departments table to find the name of the employee, including first_name and last name, department ID and name of departments.
`select first_name, last_name, department_id, department_name from employees join departments using(department_id);`

## 3. Write a SQL query to make a join with three tables employees, departments and locations to find the name, including first_name and last_name, jobs, department name and ID, of the employees working in London.
`select e.first_name, e.last_name, e.job_id, e.department_id, d.department_name from employees e join departments d on (e.department_id = d.department_id) join locations l on (l.location_id = d.location_id) where l.city = 'London';`

## 4. Write a query to make a join with two tables employees and itself to find the employee id, last_name as Employee along with their manager_id and last name as Manager.
`select W1.employee_id AS "Emp_id", W1.last_name AS "Employee", W2.employee_id AS "MGR_ID", W2.last_name AS "Manager" from employees W1 join employees W2 on (W1.manager_id = W2.employee_id);`

## 5. Write a query to make a join with a table employees and itself to find the name, including first_name and last_name and hire date for those employees who were hired after the employee Jones.
`select e.first_name, e.last_name, e.hire_date from employees e join employees d on (d.last_name = 'Jones') where d.hire_date < e.hire_date;`

## 6. Write a query to make a join with two tables employees and departments to get the department name and number of employees working in each department.
`select department_name AS "Department name", count(*) AS "Number of employees" from departments inner join employees on (employees.department_id= departments.department_id) group by departments.department_id, department_name order by department_name;`

## 7. Write a query to make a join to find the employee ID, job title and number of days an employee worked, for all the employees who worked in a department which ID is 90.
`select employee_id, job_title, end_date - start_date Days from job_history natural join jobs where department_id = 90;`

## 8. Write a query to make a join with two tables employees and departments to display the department ID, department name and the first name of the manager.
`select d.department_id, d.department_name, e.manager_id, e.first_name from departments d inner join employees e on(d.manager_id = e.employee_id);`

## 9. Write a query to make a join with three tables departments, employees, and locations to display the department name, manager name, and city.
`select d.department_name, e.employee_id, l.city from departments d join employees e on(d.manager_id = e.employee_id) join locations l using(location_id);`

## 10. Write a query to make a join with two tables employees and jobs to display the job title and average salary of employees.
`select job_title, avg(salary) from jobs natural join employees group by job_title;`

## 11. Write a query to make a join with two tables employees and jobs to display the job title, employee name, and the difference between salary and the minimum salary of the employees.
`select j.job_title, e.first_name, e.salary, j.min_salary, (e.salary - j.min_salary) as "Salary - Min_Salary" from employees e natural join jobs j;`

## 12. Write a query to make a join with two tables job_history and employees to display the status of employees who is currently drawing the salary above 10000.
`select j.* from job_history j join employees e on(j.employee_id = e.employee_id) where e.salary > 10000;`

## 13. Write a query to make a join with two tables employees and departments to display department name, first_name and last_name, hire date and salary for all the managers who achieved a working experience is more than 15 years.
`select department_name, first_name, last_name, salary, hire_date, date_part('year', age(now(), hire_date)) as "Expirence" from departments d join employees e on(d.manager_id = e.employee_id) where date_part('year', age(now(), hire_date)) > 15;`
