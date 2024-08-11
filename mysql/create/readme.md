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