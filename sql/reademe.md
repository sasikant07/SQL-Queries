## 1. SQL Query to update DateOfJoining to 15-jul-2012 for empid = 1
`UPDATE EMPLOYEE SET DATEOFJOINING="15-JUL-2012" Where EMPID=1;`

## 2.SQL query to select all sudent name where the age is greater than 22
`SELECT * FROM STUDENT WHERE AGE > 22;`

## 3. SQL query to find all employee with salary between 400000 and 800000
`SELECT * FROM EMPLOYEE WHERE SALARY BETWEEN 40000 AND 800000;`

## 4.SQL query to find name of employee begining with S.
`SEELECT * FROM EMPLOYEE WHERE FIRSTNAME LIKE "S%"`

## 5. SQL query to ddisplay full name (i.e Conact First name & last name)
`SELECT CONCAT(FIRSTNAMR, LASTNAME) FROM EMPLOYEE;`
`SEELECT FIRSTNAME ||''|| LASTNAME FROM EMPLOYEE;`

## 6. Write a query to fetch details of employees whose EMPLOYEE Firstname ends with as alphabet "A" and contains 4 alphabets.
`SELECT * FROM EMPLOYEE WHERE FIRSTNAME LIKE "____A";`

## 7. Write a query to fetch details of all employees excluding the employees with first names, "ANUSHKA" amd "SOMNATH" from the Employee table
`SELECT * FROM EMPLOYEE WHERE FIRSTNAME="ANUSHKA" OR FIRSTNAME="SOMNATH";`
`SELECT * FROM EMPLOYEE WHERE FIRSTNAME IN("ANUSHKA", "SOMNATH");`

## 8. SQL query to display the current date;
`SELECT SYSDATE, CURRENT_DATE, CURRENT_TIMESTAMPS, SYSTIMESTAMP FROM DUAL;`

## 9. SQL query to get day of last day of the previous month
`SELECT TO_CHAR(LAST_DAY(ADD_MONTHS(SYSDATE, -1)), "DAY) FROM DUAL;`

## 10. Write an SQL query to fetch the employee FIRST names and replace the A with "@"
`SELECT REPLACE(FIRSTNAME, "A", "@") FROM EMPLOYEE;`

