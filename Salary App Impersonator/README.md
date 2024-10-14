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


### Creating `quality_of_work` Table

```sql
CREATE TABLE quality_of_work (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    days_worked INTEGER,
    hrs_worked INTEGER,
    task_status TEXT
);

