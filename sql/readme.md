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

## 11. Write an SQL query to fetch the domain from an email address
`SELECT SUBSTR(EMAILID, INSTR(EMAILID, "@")+1) FROM EMPLOYEE;`

## 12. Write an SQL query to update the employee names by removing leading and trailing spaces
`UPDATE EMPLOYEE SET FIRSTNAME = LTRIM(RTRIM(FIRSTNAME));`

## 13. Write an SQL query to fetch all the employee details from EMployee Table who joined in the year 2020
`SELECT * FROM EMPLOYEE WHERE DATEOFJOINING BETWEEN "1-JAN-2020" AND "31-DEC-2020";`
`SELECT * FROM EMPLOYEE WHERE TO_CHAR(DATEOFJOINING, "YYYY") = "2020";`

## 14. Write an SQL query to fetch only odd rows / Even rows from the table
`SELECT * FROM EMPLOYEE WHERE MODE(EMPID, 2) = 0;`
`SELECT * FROM EMPLOYEE WHERE MODE(EMPID, 2)! = 0;`

## 15. Write an SQL query to create a new table with data and structure copied from another table
`CREATE TABLE emp AS (SELECT * FROM EMPLOYEE);`

## 16. Write an SQL query to create an empty tabel with the same structure as some other table
`CREATE TABLE EMP2 AS (SELECT * FROM EMPLOYEE where 1=0);`

## 17. Write an SQL query to fetch top 3 HIGHEST salaries
`SELECT SALARY FROM (SELECT DISTINCT SALARY FROM EMPLOYEE ORDER BY SALARY DESC) WHERE ROWNUM < 4;`

## 18. Find the first employee and laste employee from Employee Table
`SELECT * FROM EMPLOYEE WHERE EMPIF = (SELECT MIN(EMPID) FROM EMPLOYEE);`

## 19. Find the first employee and last employee from employee table
`SELECT * FROM EMPLOYEE WHERE EMPID = (SELECT MAX (EMPID) FROM EMPLOYEE);`

## 20. Write a query to fetch the department-wise count of employees sorted by department's account in ascending order
`SELECT DEPT, COUNT(*) FROM EMPLOYEE GROUP BY DEPT ORDER by COUNY (*);`

## 21. Write a query to retrive Departments who have less than 4 employees working in it
`SELECT DEPT, COUNT(*) FROM EMPLOYEE GROUP BY DEPT HAVING COUNT (*) < 4;`

## 22. Write a query to retrieve Depatmeny wise MAximum Salary
`SEELCT DEPT, MAX(SALARY) FROM EMPLOYEE GROUP BY DEPT;`

## 23. Write a query to Employee earning maximum salary in his department
`SELECT * FROM EMPLOYEE E! JOIN(SELECT DEPT, MAX(SALARY) SAL FROM EMPLOYEE GROUP BY DEPT ) E2 ON E1.DEPT = E2.DEPT AND E1.SALARY = E2.SAL;`

## 24. Write an SQL query to fetch the first 50% records from a table
`SEELCT * FROM EMPLOYEE WHERE ROWNUM <= (SEELCT COUNT (*) FROM EMPLOYEE)/2;`

## 25. Query to fetch details of employees not having computer
`SELECT * FROM EMPLOYEE WHERE COMPID IS NULL;`

## 26. Query to fetch employee details along with the computer details who have been assigned with a computer
`SELECT * EMPLOYEE E JOIN COMPUTER C ON E>COMPID = C.COMPID;`

## 27. Fetch all employee details along with the computer anme assigned to them
`SELCT E.EMPID, E>FRISTNAME || "" || E>LASTNAME, NVL(C>BRAND, "NOT ASSIGNED") FROM EMPLOYEE E LEFT JOIN COMPUTER C ON E.COMPID = C.OMPID;`

## 28. SELECT all computer Details alongwith employee name using it


## 29. DELETE duplicate records from a table
`DELETE FROM DUPLICATE WHERE WHERE EMPID IN(SELECT D1.EMPID FROM DUPLICATE D! JOIN DUPLICATE D@ ON D1.FIRSTNAME = D2.FIRSTNAME AND D1.LASTNAME = D2.LASTNAME AND D1.SALARY = D2.SALARY AND D1.MANAGERID = D2.MANAGERID AND D1.DATEOFJOININGID = D2.JDATEOFJOINING AND D1.EMPID > D2. EMPID);`

## 20. Find Nth Highest salary
`SELECT E1.SALARY, COUNT(DINTICT E2.SALARY) FROM EMPLOYEE E1 JOIN EMPLOYEE E2 ON e1.SALARY <= E2.SALRY GROUP BY E1.SALRY HAVING COUNT (DISTINCT E2.SALRY) = N;`

