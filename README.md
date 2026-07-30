# HR_DB

1. What is Data?

Data means raw facts or information that can be stored and processed.

Examples:

Employee Name → Arun
Employee ID → 101
Department → IT
Salary → $4,000
Age → 30

Data = Raw facts and information

2. What is a Database?

A database is an organized collection of data that allows us to store, retrieve, update, and manage information.

Example:

HR Database
│
├── Employees
├── Departments
├── Salaries
├── Attendance
└── Performance

Database = Organized collection of data

3. What is DBMS?

DBMS = Database Management System

A DBMS is software used to create, store, manage, retrieve, update, and delete data.

Examples
MySQL
Oracle
Microsoft SQL Server
PostgreSQL
SQLite
DBMS performs
CREATE
INSERT
SELECT
UPDATE
DELETE

DBMS = Software used to manage databases

4. What is RDBMS?

RDBMS = Relational Database Management System

An RDBMS stores data in tables and establishes relationships between tables.

Example:

Employees
Employee_ID	Name	Department_ID
101	Arun	10
102	Kumar	20
103	Priya	10
Departments
Department_ID	Department_Name
10	IT
20	HR

The Department_ID connects the two tables.

Examples of RDBMS
MySQL
Oracle Database
SQL Server
PostgreSQL

RDBMS = DBMS that stores related data in tables

5. What is SQL?

SQL = Structured Query Language

SQL is a language used to communicate with relational databases.

We use SQL to:

Create databases
Create tables
Insert data
Retrieve data
Update data
Delete data
Filter data
Join tables
Analyze data
Example
SELECT *
FROM employees;

This retrieves all records from the employees table.

SQL = Language used to communicate with databases

6. SQL vs MySQL
SQL	MySQL
SQL is a language	MySQL is database software
Used to write queries	Executes SQL queries
Defines database commands	Manages databases
Not itself a database	An RDBMS
Example: SELECT	Example: MySQL Server
Easy way to remember
SQL   → Language
MySQL → RDBMS Software

Example:

SELECT employee_id, name
FROM employees;

The above is SQL code, and MySQL can execute it.

7. SQL Commands

SQL commands are generally divided into five categories.

DDL – Data Definition Language

Used to define database objects.

CREATE
ALTER
DROP
TRUNCATE
RENAME

Example:

CREATE TABLE employees (
    employee_id INT,
    name VARCHAR(100)
);
DML – Data Manipulation Language

Used to modify data.

INSERT
UPDATE
DELETE

Example:

INSERT INTO employees
VALUES (101, 'Arun');
DQL – Data Query Language

Used to retrieve data.

SELECT

Example:

SELECT *
FROM employees;
DCL – Data Control Language

Used for permissions.

GRANT
REVOKE
TCL – Transaction Control Language

Used to manage transactions.

COMMIT
ROLLBACK
SAVEPOINT
Summary
Category	Full Form	Commands
DDL	Data Definition Language	CREATE, ALTER, DROP, TRUNCATE
DML	Data Manipulation Language	INSERT, UPDATE, DELETE
DQL	Data Query Language	SELECT
DCL	Data Control Language	GRANT, REVOKE
TCL	Transaction Control Language	COMMIT, ROLLBACK, SAVEPOINT
8. SQL Syntax

Syntax means the rules used to write SQL statements correctly.

Basic syntax
SELECT column_name
FROM table_name
WHERE condition;
Example
SELECT name, salary
FROM employees
WHERE salary > 3000;

This returns employees whose salary is greater than $3,000.

Another example
SELECT *
FROM employees
ORDER BY salary DESC;

This displays employees from highest salary to lowest salary.

9. SQL Comments

Comments are notes inside SQL code. They are not executed by the database.

Single-line comment
-- Display all employees
SELECT *
FROM employees;
MySQL # comment
# Display all employees
SELECT *
FROM employees;
Multi-line comment
/*
This query displays
all employee records
*/

SELECT *
FROM employees;

Comments are useful for documenting SQL code.

10. Database and Tables

A database can contain multiple tables.

Example:

HR_Database
│
├── Employees
├── Departments
├── Jobs
├── Salaries
└── Attendance
Create database
CREATE DATABASE hr_database;
Select database
USE hr_database;
Create table
CREATE TABLE employees (
    employee_id INT,
    name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);
11. Rows and Columns

Consider this table:

Employee_ID	Name	Department	Salary
101	Arun	IT	$4,000
102	Kumar	HR	$3,500
103	Priya	Finance	$4,200
Row

A row represents one complete record.

101 | Arun  | IT      | $4,000

There are 3 rows in the example.

Column

A column represents a field or attribute.

Employee_ID
Name
Department
Salary

There are 4 columns.

Remember

Row = Record
Column = Field / Attribute

12. Primary Key

A Primary Key uniquely identifies each record in a table.

Example:

CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50)
);

Here:

employee_id → PRIMARY KEY

Example:

Employee_ID	Name
101	Arun
102	Kumar
103	Priya

Every employee has a unique employee_id.

Primary Key Rules
Must uniquely identify records.
Cannot contain NULL.
A table has one primary-key constraint.
A primary key can contain multiple columns (composite primary key).
13. Foreign Key

A Foreign Key creates a relationship between two tables by referencing a key in another table.

Parent table
CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(100)
);
Child table
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    department_id INT,

    FOREIGN KEY (department_id)
    REFERENCES departments(department_id)
);

Here:

departments.department_id
            ↑
            │
            │ Foreign Key relationship
            │
employees.department_id
Example

Departments

Department_ID	Department_Name
10	IT
20	HR
30	Finance

Employees

##Employee_ID	Name	Department_ID##
101	Arun	10
102	Kumar	20
103	Priya	30

departments.department_id → Primary Key

employees.department_id → Foreign Key

Primary Key vs Foreign Key
Primary Key	Foreign Key
Identifies a record uniquely	Creates a relationship between tables
Values must be unique	Values can repeat
Cannot be NULL	Can be NULL depending on table design
Usually exists in parent table	Usually exists in child table
Example: department_id in Departments	Example: department_id in Employees
