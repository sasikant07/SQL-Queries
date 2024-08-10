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

## 