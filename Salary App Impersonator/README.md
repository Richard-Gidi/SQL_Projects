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

### Creating `quality_of_work` Table

```sql
CREATE TABLE quality_of_work (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    days_worked INTEGER,
    hrs_worked INTEGER,
    task_status TEXT
);
```
### Creating `task_deadline` Table

```sql
CREATE TABLE task_deadline (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    name TEXT,
    name_of_task TEXT,
    hrs_assigned INTEGER
);
```

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

