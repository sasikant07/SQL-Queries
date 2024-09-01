## 1.Write a query to display the names (first_name, last_name) and salary for all employees whose salary is not in the range $10,000 through $15,000.

`SELECT FIRST_NAME, LAST_NAME, SALARY FROM Employees where Salary not between 10000 and 15000;`

## 2. Write a query to display the name (first_name, last_name) and department ID of all employees in departments 30 or 100 in ascending order.
`SELECT FIRST_NAME, LAST_NAME, DEPARTMENT_ID FROM Employees where DEPARTMENT_ID in(30,100) order by DEPARTMENT_ID asc;`

## 3. Write a query to display the name (first_name, last_name) and salary for all employees whose salary is not in the range $10,000 through $15,000 and are in department 30 or 100.
`SELECT FIRST_NAME, LAST_NAME, DEPARTMENT_ID, salary FROM Employees where salary not between 10000 AND 15000   AND DEPARTMENT_ID in(30,100);`

## 4. Write a query to display the name (first_name, last_name) and hire date for all employees who were hired in 1987.

`SELECT first_name, last_name, hire_date FROM employees WHERE YEAR(hire_date)  LIKE '2023%';`

## 5. Write a query to display the first_name of all employees who have both "b" and "c" in their first name.
`SELECT first_name from Employees where first_name like "%b%" and first_name like "%c%";`

## 6. Write a query to display the last name, job, and salary for all employees whose job is that of a Programmer or a Shipping Clerk, and salary is not equal to $4,500, $10,000, or $15,000.
`SELECT LAST_NAME, SALARY, JOB_ID from Employees where JOB_ID IN("IT_PROG","SHIP_CLERK") AND SALARY NOT IN(45000, 10000, 15000);`