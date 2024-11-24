https://demo.gethue.com/hue/metastore/databases?source_type=hive

-- Create database

CREATE DATABASE MCA_rollno;

-- Use the database

USE MCA_rollno;

-- Create the employee table

CREATE TABLE employee (
    emp_id INT,
    empfname STRING,
    emplname STRING,
    job STRING,
    sal FLOAT,
    deptcode INT
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE;

-- Create the department table

CREATE TABLE department (
    deptcode INT,
    deptname STRING,
    location STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE;
