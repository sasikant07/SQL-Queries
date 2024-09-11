## 1. Write a  MySQL query to find the addresses (location_id, street_address, city, state_province, country_name) of all the departments.
`select LOCATION_ID, STREET_ADDRESS, CITY, STATE_PROVINCE, COUNTRY_NAME from locations NATURAL JOIN countries;`

## 2.Write a  MySQL query to find the name (first_name, last name), department ID and name of all the employees.
`select FIRST_NAME, LAST_NAME, DEPARTMENT_ID, DEPARTMENT_NAME from employees JOIN departments USING (DEPARTMENT_ID);`

## 3. Write a  MySQL query to find the name (first_name, last_name), job, department ID and name of the employees who works in  London.
`select e.FIRST_NAME, e.LAST_NAME, e.JOB_ID, e.DEPARTMENT_ID, d.DEPARTMENT_NAME from employees e JOIN departments d ON (e.DEPARTMENT_ID = d.DEPARTMENT_ID) JOIN locations l ON (l.LOCATION_ID = d.LOCATION_ID) where LOWER(l.city) = "London";`

## 4. Write a  MySQL query to find the employee id, name (last_name) along with their manager_id and name (last_name).
`select e.EMPLOYEE_ID "EMP_ID", e.LAST_NAME "EMP_NAME", m.EMPLOYEE_ID "MGR_ID", m.LAST_NAME "MGR_NAME" from employees e JOIN employees m ON(e.MANAGER_ID = m.EMPLOYEE_ID);`

## 5. Write a  MySQL query to find the name (first_name, last_name) and hire date of the employees who was hired after 'Jones'.
`select e.FIRST_NAME, e.LAST_NAME, e.HIRE_DATE from employees e JOIN employees d ON (d.LAST_NAME = "Jones") WHERE d.HIRE_DATE < e.HIRE_DATE;`

