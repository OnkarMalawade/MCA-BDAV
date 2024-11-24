https://demo.gethue.com/hue/metastore/databases?source_type=hive

``` sql
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
```
employee.txt
```
csv
101,John,Doe,Manager,50000,1
102,Jane,Smith,Developer,30000,2
103,Mike,Brown,Tester,20000,1
104,Susan,Lee,Developer,25000,3
105,Chris,Johnson,Manager,55000,2
```
dept.txt
```
csv
1,HR,New York
2,IT,San Francisco
3,Finance,Chicago
```

```
HDFS

hdfs dfs -put employee.txt /user/hive/warehouse/MCA_rollno.db/

hdfs dfs -put dept.txt /user/hive/warehouse/MCA_rollno.db/

```

```
sql

-- Load data into employee table
LOAD DATA INPATH '/user/hive/warehouse/MCA_rollno.db/employee.txt' INTO TABLE employee;

-- Load data into department table
LOAD DATA INPATH '/user/hive/warehouse/MCA_rollno.db/dept.txt' INTO TABLE department;

```

```
SELECT * FROM employee;
SELECT * FROM department;

SELECT * FROM employee WHERE sal > 25000;

SELECT MAX(sal) AS max_salary FROM employee;

SELECT * FROM employee
ORDER BY sal DESC, empfname ASC;

SELECT job, SUM(sal) AS total_salary
FROM employee
GROUP BY job;

SELECT e.emp_id, e.empfname, e.emplname, e.job, e.sal, d.deptname, d.location
FROM employee e
RIGHT OUTER JOIN department d
ON e.deptcode = d.deptcode;

```


