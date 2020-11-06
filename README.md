# employee-tracker

A solution for managing a company's employees using node, inquirer, and MySQL
* The command-line application allows users to:

  * Add departments, roles, employees
  * View departments, roles, employees
  * Update employee roles
  * View employees by manager
  * Delete departments, roles, employees

# Visuals
![employee-tracker](Employee-Tracker.gif)

# Usage

1. Use the CLI interface to select employee management options
2. Menu options lead to additional prompts
3. Options return to the home menu.
4. Select the next option as needed.
5. Use the Exit option to close the application.

# Steps to Setup
1. Clone the repo

```bash
git clone git@github.com:beshayr2020/Employee-Tracker.git
```

2. Install dependencies

```bash
npm install
```

3. Create the database using the Schema.sql and seeds.sql files.

```
DROP DATABASE IF EXISTS employee_db;
CREATE DATABASE employee_db;
USE employee_db;

CREATE TABLE departments(
id INT AUTO_INCREMENT PRIMARY KEY,
department_name VARCHAR(30)
);

CREATE TABLE roles (
id INT AUTO_INCREMENT PRIMARY KEY,
title VARCHAR(30),
salary DECIMAL(8,2),
department_id INT,
FOREIGN KEY(department_id) REFERENCES departments(id)
);

CREATE TABLE employees(
id INT AUTO_INCREMENT PRIMARY KEY,
first_name VARCHAR(30) NOT NULL,
last_name VARCHAR(30) NOT NULL,
role_id INT,
manager_id INT,
FOREIGN KEY(role_id) REFERENCES roles(id),
FOREIGN KEY(manager_id) REFERENCES employees(id)
);
```

```
INSERT INTO departments(department_name)
VALUES ('Management'),
('Sales'),
('Warehouse'),
('Human Resources'),
('Quality Control');

INSERT INTO roles(title)
VALUES('Regional Manager'),
('Sales Rep'),
('HR Rep');

INSERT INTO employees(first_name, last_name)
VALUES('Pam', 'Beesly'),
('Michael', 'Scott'),
('Jim', 'Halpert');

```

4. Run Server

```bash
node server.js
```

# Links to Project

##### GitHub
[employee-tracker](https://beshayr2020.github.io/Employee-Tracker/)
