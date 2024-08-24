# MYSQL QUERIES

# CREATE TABLE QUERIES

## 1. Create a MySQL table named countries with columns country_id, country_name, and region_id
`
    CREATE TABLE countries (
        COUNTRY_ID varchar(20),
        COUNTRY_NAME varchar(40),
        REGION_ID decimal(10, 0)
    );
`

## 2.Create a MySQL table named countries if it doesn't already exist
`
    CREATE TABLE IF NOT EXISTS countries (
        country_id varchar(20),
        country_name varchar(40),
        region_id decimal(10, 0)
    );
`

## 3. Create the structure of a MySQL table named dup_countries similar to the existing table named countries
` CREATE TABLE IF NOT EXISTS dup_countries LIKE countries;`

## 4.Create a duplicate copy of the MySQL table named countries with both structure and data, naming it dup_countries

` CREATE TABLE IF NOT EXISTS dup_countries AS SELECT * FROM countries;`

## 5. Create a MySQL table named countries with a NOT NULL constraint on certain columns
` CREATE TABLE IF NOT EXISTS countries (
    country_id varchar(20) NOT NULL,
    country_name varchar(40) NOT NULL,
    region_id decimal(10, 0) NOT NULL
);
`

## 6. Write a  MySQL query to create a table named jobs including columns job_id, job_title, min_salary, max_salary and check whether the max_salary amount exceeding the upper limit 25000.
` CREATE TABLE IF NOT EXISTS jobs (
    job_id varchar(20) NOT NULL,
    job_titile varchar(20) NOT NULL,
    min_salary decimal(6, 0),
    max_salary decimal(6, 0),
    CHECK(max_salary <= 25000)
  );
`

## 7. Write a  MySQL query to create a table named countries including columns country_id, country_name and region_id and make sure that no countries except Italy, India and China will be entered in the table
` CREATE TABLE IF NOT EXISTS countries (
    country_id varchar(20),
    country_name varchar(40) CHECK(country_name IN("Italy", "India", "China")),
    region_id decimal(10, 0)
);
`

## 8. Write a  MySQL query to create a table named job_histry including columns employee_id, start_date, end_date, job_id and department_id and make sure that the value against column end_date will be entered at the time of insertion to the format like '--/--/----'.
` CREATE TABLE IF NOT EXISTS job_history (
    employee_id varchar(20) NOT NULL,
    start_date date NOT NULL,
    end_date date NOT NULL CHECK(end_date LIKE "--/--/----"),
    department_id varchar(20) NOT NULL
);
`

## 9. Write a  MySQL query to create a table named countries including columns country_id,country_name and region_id and make sure that no duplicate data against column country_id will be allowed at the time of insertion.
` CREATE TABLE IF NOT EXISTS countries(
    country_id varchar(2) NOT NULL,
    country_name varchar(40) NOT NULL,
    region_id varchar(20) NOT NULL,
    UNIQUE(country_id)
);
`

## 10. Write a  MySQL query to create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.
`CREATE TABLE IF NOT EXISTS jobs ( 
  job_id varchar(10) NOT NULL UNIQUE, 
  ob_title varchar(35) NOT NULL DEFAULT "", 
  min_salary decimal(6,0) DEFAULT 8000, 
  max_salary decimal(6,0) DEFAULT NULL
);
`

## 11. Write a  MySQL query to create a table named countries including columns country_id, country_name and region_id and make sure that the country_id column will be a key field which will not contain any duplicate data at the time of insertion.
`CREATE TABLE IF NOT EXISTS countries (
  country_id varchar(20) NOT NULL UNIQUE PRIMARY KEY,
  country_name varchar(40) NOT NULL,
  region_id decimal(10, 0) NOT NULL
);
`
## 12. Write a  MySQL query to create a table countries including columns country_id, country_name and region_id and make sure that the column country_id will be unique and store an auto incremented value.
`CREATE TABLE IF NOT EXISTS countries (
  country_id integer NOT NULL UNIQUE AUTO_INCREMENT PRIMARY KEY,
  country_name varchar(40) NOT NULL,
  region_id decimal(10, 0) NOT NULL
);
`
## 13. Write a  MySQL query to create a table countries including columns country_id, country_name and region_id and make sure that the combination of columns country_id and region_id will be unique.
`CREATE TABLE IF NOT EXISTS countries (
  country_id integer NOT NULL UNIQUE AUTO_INCREMENT,
  country_name varchar(40) NOT NULL,
  region_id decimal(10, 0) NOT NULL,
  PRIMARY KEY (country_id, region_id)
  
);
`
## 14. Write a  MySQL query to create a table job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key column job_id contain only those values which are exists in the jobs table.
`
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+

CREATE TABLE IF NOT EXISTS job_history (
    employee_id varchar(20) NOT NULL PRIMARY KEY,
    start_date date NOT NULL,
    end_date date NOT NULL,
    job_id varchar(20) NOT NULL,
    department_id varchar(20) NOT NULL,
    FOREIGN KEY(job_id) REFERENCES jobs(job_id)
);
`

## 15. Write a MySQL query to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key columns combined by department_id and manager_id columns contain only those unique combination values, which combinations are exists in the departments table.

Assume the structure of departments table below.

+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | NO   | PRI | 0       |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+

`CREATE TABLE IF NOT EXISTS departments (
  department_id decimal(6, 0) NOT NULL DEFAULT 0,
  department_name varchar(10),
  manager_id decimal(6, 0) NOT NULL DEFAULT 0,
  location_id decimal(6, 0),
  PRIMARY KEY(department_id, manager_id)
);

CREATE TABLE IF NOT EXISTS employees (
  employee_id decimal(6, 0) NOT NULL PRIMARY KEY,
  first_name varchar(20) NOT NULL,
  last_name varchar(20) NOT NULL,
  email varchar(20) NOT NULL,
  phone_number varchar(20) NOT NULL,
  hore_date date NOT NULL,
  job_id decimal(6, 0) NOT NULL,
  salry decimal(6, 0) NOT NULL,
  commission decimal(4, 0) NULL,
  manager_id decimal(6, 0) NOT NULL,
  department_id decimal(6, 0) NOT NULL,
  FOREIGN KEY(department_id, manager_id) REFERENCES departments(department_id, manager_id)
);
`

## 16. Write a  MySQL query to create a table employees including columns employee_id, first_name, last_name,  email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column department_id, reference by the column department_id of departments table, can contain only those values which are exists in the departments table and another foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables.

"A foreign key constraint is not required merely to join two tables. For storage engines other than InnoDB, it is possible when defining a column to use a REFERENCES tbl_name(col_name) clause, which has no actual effect, and serves only as a memo or comment to you that the column which you are currently defining is intended to refer to a column in another table." - Reference dev.mysql.com

Assume that the structure of two tables departments and jobs.

+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | YES  |     | NULL    |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+


+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
Sample Solution:

`
CREATE TABLE IF NOT EXISTS departments (
  department_id decimal(6, 0) NOT NULL DEFAULT 0,
  department_name varchar(10),
  manager_id decimal(6, 0) NOT NULL DEFAULT 0,
  location_id decimal(6, 0),
  PRIMARY KEY(department_id, manager_id)
);

CREATE TABLE IF NOT EXISTS jobs (
  job_id decimal(6, 0) NOT NULL PRIMARY KEY,
  job_title varchar(10) NOT NULL,
  min_salary decimal(6, 0) NULL,
  max_salary decimal(6, 0) NULL
);

CREATE TABLE IF NOT EXISTS employees (
  employee_id decimal(6, 0) NOT NULL PRIMARY KEY,
  first_name varchar(20) NOT NULL,
  last_name varchar(20) NOT NULL,
  email varchar(20) NOT NULL,
  phone_number varchar(20) NOT NULL,
  hore_date date NOT NULL,
  job_id decimal(6, 0) NOT NULL,
  salry decimal(6, 0) NOT NULL,
  commission decimal(4, 0) NULL,
  manager_id decimal(6, 0) NOT NULL,
  department_id decimal(6, 0) NOT NULL,
  FOREIGN KEY(department_id) REFERENCES departments(department_id),
  FOREIGN KEY(job_id) REFERENCES jobs(job_id)
);
`

## 17. Write a  MySQL query to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The  InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON UPDATE CASCADE action allows you to perform cross-table update and ON DELETE RESTRICT action reject the deletion. The default action is ON DELETE RESTRICT.

Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
Sample Solution:
`
CREATE TABLE IF NOT EXISTS employees ( 
EMPLOYEE_ID decimal(6,0) NOT NULL PRIMARY KEY, 
FIRST_NAME varchar(20) DEFAULT NULL, 
LAST_NAME varchar(25) NOT NULL, 
EMAIL varchar(25) NOT NULL, 
PHONE_NUMBER varchar(20) DEFAULT NULL, 
HIRE_DATE date NOT NULL, 
JOB_ID varchar(10) NOT NULL, 
SALARY decimal(8,2) DEFAULT NULL, 
COMMISSION_PCT decimal(2,2) DEFAULT NULL, 
MANAGER_ID decimal(6,0) DEFAULT NULL, 
DEPARTMENT_ID decimal(4,0) DEFAULT NULL, 
FOREIGN KEY(DEPARTMENT_ID) REFERENCES  departments(DEPARTMENT_ID),
FOREIGN KEY(JOB_ID) REFERENCES  jobs(JOB_ID)
);
`

## 18. Write a  MySQL query to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The  InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE CASCADE that lets you allow to delete records in the employees(child) table that refer to a record in the jobs(parent) table when the record in the parent table is deleted and the ON UPDATE RESTRICT actions reject any updates.

Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
Sample Solution:
`
CREATE TABLE IF NOT EXISTS employees ( 
EMPLOYEE_ID decimal(6,0) NOT NULL PRIMARY KEY, 
FIRST_NAME varchar(20) DEFAULT NULL, 
LAST_NAME varchar(25) NOT NULL, 
JOB_ID INTEGER, 
SALARY decimal(8,2) DEFAULT NULL, 
FOREIGN KEY(JOB_ID) REFERENCES  jobs(JOB_ID)
<!-- ON DELETE SET NULL ON UPDATE SET NULL -->
ON DELETE CASCADE ON UPDATE RESTRICT
);
`
## 19. Write a  MySQL query to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The  InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE SET NULL action will set the foreign key column values in the child table(employees) to NULL when the record in the parent table(jobs) is deleted, with a condition that the foreign key column in the child table must accept NULL values and the ON UPDATE SET NULL action resets the values in the rows in the child table(employees) to NULL values when the rows in the parent table(jobs) are updated.

Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;


+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
Sample Solution:
`
CREATE TABLE IF NOT EXISTS employees ( 
EMPLOYEE_ID decimal(6,0) NOT NULL PRIMARY KEY, 
FIRST_NAME varchar(20) DEFAULT NULL, 
LAST_NAME varchar(25) NOT NULL, 
JOB_ID INTEGER, 
SALARY decimal(8,2) DEFAULT NULL, 
FOREIGN KEY(JOB_ID) REFERENCES  jobs(JOB_ID)
ON DELETE SET NULL ON UPDATE SET NULL
);

`

## 20. Write a MySQL query to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE NO ACTION and the ON UPDATE NO ACTION actions will reject the deletion and any updates.

Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;


+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
Sample Solution:

`
CREATE TABLE IF NOT EXISTS employees ( 
EMPLOYEE_ID decimal(6,0) NOT NULL PRIMARY KEY, 
FIRST_NAME varchar(20) DEFAULT NULL, 
LAST_NAME varchar(25) NOT NULL, 
JOB_ID INTEGER NOT NULL, 
SALARY decimal(8,2) DEFAULT NULL, 
FOREIGN KEY(JOB_ID) REFERENCES  jobs(JOB_ID)
ON DELETE NO ACTION ON UPDATE NO ACTION
);
`