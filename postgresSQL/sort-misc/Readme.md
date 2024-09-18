## 1. Write a query to display the name, including first_name and last_name and salary for all employees whose salary is out of the range between $10,000 and $15,000.
`select first_name, last_name, salary from employees where salary not between 10000 and 15000;`

## 2. Write a query to display the name, including first_name and last_name, and department ID who works in the department 30 or 100 and arrange the result in ascending order according to the department ID.
`select first_name, last_name, department_id from employees where department_id in(30, 100) order by department_id asc;`

## 3. Write a query to display the name, including first_name and last_name, and salary who works in the department either 30 or 100 and salary is out of the range between $10,000 and $15,000.
`select first_name, last_name, salary, department_id from employees where salary not between 10000 and 15000 and department_id in(30, 100);`

## 4. Write a query to display the name, including first_name and last_name and hire date for all employees who were hired in 1987
`SELECT first_name, last_name, hire_date FROM employees WHERE TO_CHAR(hire_date, 'YYYY')  LIKE '%87';`

## 5. Write a query to get the first name of the employee who holds the letter 'c' and 'e' in the first name.
`select first_name from employees where first_name LIKE '%c%' and first_name LIKE '%e%';`

## 6. Write a query to display the last name, job, and salary for all those employees who hasn't worked as a Programmer or a Shipping Clerk, and not drawing the salary $4,500, $10,000, or $15,000.
`SELECT last_name, job_id, salary FROM employees WHERE job_id NOT IN ('IT_PROG', 'SH_CLERK') AND salary NOT IN (4500,10000, 15000);`

