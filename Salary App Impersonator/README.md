# Salary Calculation App

## Overview

The **Salary Calculation App** is a SQL-based project designed to track and manage worker data, work quality, and salary payments for a tech startup. This project simulates a database-driven salary management system, with the capability to calculate salaries based on the number of hours worked, work quality, and assigned tasks. The system also allows for various queries, including analysis of worker data and task completion status.

## Features

- **Workers Table**: Stores personal and professional details of workers such as name, age, department, gender, and address.
- **Quality of Work Table**: Tracks the quality of work, days worked, and hours worked by each employee, as well as the status of tasks (Completed or Pending).
- **Task Deadline Table**: Records task assignments, hours allocated to tasks, and tracks deadlines for workers.
- **SQL Queries**: Perform operations like counting workers, analyzing department statistics, calculating minimum and maximum worker ages, checking task completion, and calculating salary based on work hours.

## Database Schema

### 1. Workers Table (`workers`)
We create a table to accommodate basic worker information and declare the data types for each
```sql 
CREATE TABLE workers (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    name TEXT,
    age INTEGER,
    department TEXT,
    gender TEXT,
    address TEXT(40)
);
```

### 2. Creating `quality_of_work` Table
We create a table for the number of days worked, hours worked and whether or not they have completed their assigned task
```sql
CREATE TABLE quality_of_work (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    days_worked INTEGER,
    hrs_worked INTEGER,
    task_status TEXT
);
```
### 3. Creating `task_deadline` Table
We create a table to contain information on the task assigned each worker and declare the data types for each
```sql
CREATE TABLE task_deadline (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    name TEXT,
    name_of_task TEXT,
    hrs_assigned INTEGER
);
```

# Sample Data

### Inserting Data into the `workers` Table

```sql
INSERT INTO workers (name, age, department, gender, address) 
VALUES 
    ("Keren-Happuch Adu Yeboah", 45, "Data Engineering", "Female", "Nungua"),
    ("Richard Gidi", 38, "Data Science", "Male", "Santor"),
    ("Laura Eyi Kartey", 31, "Data Analysis", "Female", "Haatso"),
    ("Isaac Annan", 61, "Data Science", "Male", "Winneba"),
    ("Susana Ama Gatogo Abban", 33, "Data Engineering", "Female", "Ablekuma"),
    ("Rabiatu Ibrahim", 38, "Data Science", "Female", "Madina"),
    ("Dannette Kwanyo Zotorvie", 20, "Data Engineering", "Female", "Tema"),
    ("Quartey Phoebe", 22, "Accounting", "Female", "West Legon"),
    ("Ellen Essuamah Asante", 33, "Data Engineering", "Male", "Madina"),
    ("Napoleon Quartey-Papafio", 38, "Accounting", "Male", "Osu"),
    ("Samuel Osei Boadu", 20, "Marketing", "Female", "Kasoa"),
    ("Firdaus Mohammed", 22, "Data Science", "Female", "Gbawe Topbase");
```

### Inserting Data into the `quality_of_work` Table
```sql
INSERT INTO quality_of_work (days_worked, hrs_worked, task_status) 
VALUES 
    (20, 10, "Completed"),
    (15, 8, "Pending"),
    -- Additional entries here
    (25, 12, "Pending");
```

### Inserting Data into the 'task_deadline` Table
```sql
INSERT INTO task_deadline (name, name_of_task, hrs_assigned) 
VALUES 
    ("Keren-Happuch Adu Yeboah", "Data and information visualization", 12),
    ("Richard Gidi", "Clean dataset", 10),
    -- Additional entries here
    ("Firdaus Mohammed", "Overseeing data quality control", 12);
```

### Counting Workers, Departments, and Unique Addresses

```sql
SELECT COUNT(DISTINCT address), COUNT(name) AS total_workers, COUNT(DISTINCT department) 
FROM workers;
```

### Finding Minimum and Maximum Worker Age

```sql
SELECT MIN(age) AS MIN_AGE, MAX(age) AS MAX_AGE 
FROM workers;
```

### Calculating Average Hours to Finish Tasks by Department

```sql
SELECT department, AVG(hrs_worked) AS avg_hours_to_finish
FROM quality_of_work
JOIN workers ON quality_of_work.id = workers.id
WHERE task_status = 'Completed'
GROUP BY department;
```

### Calculating Average Salary for Each Department

```sql
SELECT a.department, AVG(hrs_worked * 13.53 * days_worked) AS AVERAGE_SALARY
FROM workers a
JOIN quality_of_work ON a.id = quality_of_work.id
GROUP BY a.department;
```

# POWER BI


## Insights from The Best Company Ltd. Dashboard

### Company Overview
**The Best Company Ltd.** is a tech startup that actively promotes female participation in technology roles, resulting in a workforce that consists of more females than males. This commitment to diversity is reflected in the company's current structure, which is relatively small, with only 11 employees. 

![image](https://github.com/user-attachments/assets/3678363d-6c48-45ce-99d1-ea8f90a272eb)


### Workforce Composition
- **Gender Representation**: The workforce includes 72.73% female employees (8 out of 11), emphasizing the company's initiative to empower women in tech.
- **Departmental Distribution**: The largest team is in **Data Science** (4 personnel), which aligns with the company's focus on leveraging data-driven solutions. In contrast, there is only one **Data Analyst**, suggesting that the company prioritizes developing robust data science capabilities over broader analytical roles at this stage.

### Salary Insights
- The average salary for employees is currently on the lower end, a common scenario for startups that are still in the early stages of establishing their financial footing.
- Notably, there is a correlation between age and salary, where older employees tend to earn more due to their accumulated experience, providing valuable insights that can drive the company's growth.

![image](https://github.com/user-attachments/assets/d2dc41dc-cfad-46c3-b471-745b96cf2a70)


### Hours Worked Analysis
- **Data Analysis**: Although assigned only **4 hours** of work, analysts are putting in **8 hours**, indicating a strong work ethic and a commitment to completing their tasks. This overextension may lead to burnout if not addressed.
- **Data Science**: Conversely, employees in data science are assigned **12.25 hours** but actually work **8.75 hours**, resulting in more **pending tasks**. This discrepancy may suggest inefficiencies or challenges within the department that need to be managed to improve productivity.

### Task Insights
- **Data Quality Control**: The highest hours worked (12 hours) in this area underscore the critical importance of data quality in ensuring the reliability of models and analyses. This focus on data integrity is essential for the company's commitment to building trustworthy solutions.
- **Dashboard Maintenance**: With only **5 hours** spent on maintaining dashboards, it indicates that these tools are already well-established, allowing the team to allocate more time to higher-priority tasks like data quality and analysis.


![image](https://github.com/user-attachments/assets/8b2653c6-dbc0-4231-b8f0-3d5f4446a220)


### Conclusion
In summary, The Best Company Ltd. is navigating the challenges of a startup environment while making strategic choices in workforce composition, salary structures, and task management. The focus on data quality and the empowerment of female employees in tech are commendable, setting a strong foundation for future growth and success.
