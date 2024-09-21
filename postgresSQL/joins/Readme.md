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