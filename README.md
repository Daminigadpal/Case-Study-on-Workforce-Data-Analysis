# Salary and Remote Work Trends Across Job Titles and Company Locations

## 📌 Project Overview

This project analyzes salary and remote-work trends across different job titles, experience levels, employment types, countries, and company sizes using **Microsoft SQL Server**.

The objective is to extract meaningful business insights from salary data and support decisions related to:

* Salary benchmarking
* Workforce planning
* Remote-work optimization
* Cost management
* Employee retention
* Career pathing
* Domain and role selection

---

## 🛠️ Technologies Used

* **Microsoft SQL Server (MS-SQL Server)**
* **SQL**
* **SSMS (SQL Server Management Studio)**
* **Excel** — source dataset
* **CTE (Common Table Expressions)**
* **Window Functions**
* **Aggregate Functions**
* **CASE Statements**
* **Subqueries**
* **Stored Procedures**

---

## 📂 Dataset

The project uses the **Salaries** dataset containing **13,972 records**.

### Dataset Columns

| Column               | Description                     |
| -------------------- | ------------------------------- |
| `work_year`          | Year of employment data         |
| `experience_level`   | Employee experience level       |
| `employment_type`    | Type of employment              |
| `job_title`          | Employee's job title            |
| `salary`             | Salary in original currency     |
| `salary_currency`    | Original salary currency        |
| `salary_in_usd`      | Salary converted to USD         |
| `employee_residence` | Employee's country of residence |
| `remote_ratio`       | Percentage of remote work       |
| `company_location`   | Company's location              |
| `company_size`       | Size of the company             |

### Experience Levels

* **EN** — Entry-level
* **MI** — Mid-level
* **SE** — Senior-level
* **EX** — Executive-level

### Remote Ratio

* **0** — Fully in-office
* **Intermediate values** — Hybrid
* **100** — Fully remote

### Company Size

* **S** — Small
* **M** — Medium
* **L** — Large

---

## 🎯 Business Objectives

The project focuses on answering business questions such as:

1. How are employees distributed across different company sizes?
2. Which job titles have the highest average salaries?
3. Which countries provide higher salaries for mid-level employees?
4. Which locations offer the highest and lowest salaries for senior employees?
5. How have salaries changed between 2023 and 2024?
6. Which countries experienced the highest entry-level salary growth?
7. How can remote-work policies be optimized?
8. How do salaries differ across experience levels?
9. Which years provide the highest average salary for different job titles?
10. What is the proportion of full-time and part-time employees?
11. Which countries offer highly paid remote manager positions?
12. Which countries have the largest number of large companies?
13. What percentage of fully remote employees earn more than $100,000?
14. Which locations pay entry-level employees above the market average?
15. Which countries provide the highest salary for each job title?
16. Which countries show sustained salary growth?
17. How has remote work changed between 2021 and 2024?
18. How did salaries increase by experience level and job title?
19. How can role-based access be implemented using experience levels?
20. Which career domains provide higher salary opportunities?

---

## 🔍 SQL Methodologies Used

### 1. Filtering

Used `WHERE` clauses to filter records based on:

* Year
* Experience level
* Employment type
* Salary
* Remote ratio
* Country
* Company size

### 2. Aggregation

Used:

```sql
COUNT()
SUM()
AVG()
MAX()
MIN()
```

to calculate business metrics.

### 3. GROUP BY

Used to analyze salary and employee trends by:

* Job title
* Country
* Experience level
* Company size
* Employment type

### 4. HAVING

Used to filter aggregated results, such as job titles or countries having more than a specified number of employees.

### 5. CASE Statements

Used for:

* Salary adjustments
* Employee classification
* Domain recommendations
* Full-time/part-time calculations

### 6. Common Table Expressions

CTEs were used to simplify complex salary-growth and comparison calculations.

Example:

```sql
WITH SalaryData AS
(
    SELECT
        job_title,
        work_year,
        AVG(salary_in_usd) AS average_salary
    FROM salaries
    GROUP BY job_title, work_year
)
SELECT *
FROM SalaryData;
```

### 7. Window Functions

Functions such as `RANK()` were used to identify the highest-paying year or country for each job title.

### 8. Subqueries

Subqueries were used to compare individual country salaries against overall market averages.

### 9. Stored Procedures

A stored procedure was created to retrieve employees according to their experience level.

Example:

```sql
CREATE PROCEDURE GetEmployeesByExperience
    @ExperienceLevel VARCHAR(10)
AS
BEGIN
    SELECT
        work_year,
        experience_level,
        employment_type,
        job_title,
        salary_in_usd,
        employee_residence,
        remote_ratio,
        company_location,
        company_size
    FROM salaries
    WHERE experience_level = @ExperienceLevel;
END;
```

Execute it using:

```sql
EXEC GetEmployeesByExperience 'SE';
```

---

## 📊 Key Analysis Areas

### Salary Analysis

The project compares:

* Average salaries
* Salary growth
* Salary differences by experience
* Salary differences by country
* Salary differences by job title
* Highest and lowest salary locations

### Remote Work Analysis

The project evaluates:

* Fully remote employees
* Hybrid employees
* In-office employees
* Remote work by experience level
* High-paying remote positions

### Employment Analysis

The analysis compares:

* Full-time employees
* Part-time employees
* Employment distribution by job title

### Geographic Analysis

Countries and company locations are compared to identify:

* High-paying locations
* Low-paying locations
* Salary growth
* Large-company concentration
* Remote opportunities

---

## 📈 Business Insights

The analysis can help organizations understand:

* Where competitive salaries are being offered
* Which job roles have stronger salary potential
* How compensation changes with experience
* Which locations are attractive for talent
* How remote work varies across employee levels
* Which countries demonstrate sustained salary growth
* Which career domains may provide better salary opportunities

---

## 💡 Actionable Recommendations

Based on the analysis, organizations can:

1. **Improve salary benchmarking**
   Compare compensation against job title, experience level, and location.

2. **Optimize remote-work policies**
   Use remote-work trends to create flexible workforce strategies.

3. **Improve workforce planning**
   Identify locations and roles with strong salary and employment trends.

4. **Control hiring costs**
   Compare salaries across countries before expanding hiring operations.

5. **Support employee retention**
   Maintain competitive compensation for experienced employees.

6. **Support career planning**
   Identify job titles and domains with stronger salary opportunities.

---

## 📁 Project Files

The project contains:

```text
Project-4/
│
├── Salaries(1).xls
├── Project-4.pdf
├── Project-4-Complete-SSMS-With-13972-Rows.sql
└── README.md
```

### SQL Script

The SQL script contains:

* Database creation
* Table creation
* Dataset insertion
* 13,972 salary records
* 20 project queries
* Data-quality checks

---

## ▶️ How to Run the Project

### Step 1 — Open SQL Server Management Studio

Open **SSMS** and connect to your SQL Server instance.

### Step 2 — Open the SQL File

Open:

```text
Project-4-Complete-SSMS-With-13972-Rows.sql
```

### Step 3 — Execute the Script

Run the script in SSMS.

It will create the database:

```sql
Salary_Remote_Work_Project
```

and the table:

```sql
dbo.salaries
```

### Step 4 — Verify the Data

Run:

```sql
SELECT COUNT(*) AS total_records
FROM dbo.salaries;
```

Expected result:

```text
13972
```

### Step 5 — Execute the Project Queries

Run the 20 analysis queries included in the SQL file.

---

## ⚠️ Important Note

If the `salaries` table has already been populated from the Excel file, **do not execute the INSERT section again**, because it will create duplicate records.

The complete SQL file already contains the dataset insertion statements.

---

## 📋 Submission Guidelines

### Format

* PowerPoint or PDF

### Length

* 1–20 slides

### Required Sections

* Introduction
* Key Findings
* Actionable Recommendations
* Methodologies
* Approaches
* Insights
* Conclusions

### Technology

* MS-SQL Server

---

## 🏁 Conclusion

This project demonstrates how SQL can be used to transform a large salary dataset into meaningful business insights.

Through filtering, aggregation, subqueries, CTEs, window functions, CASE statements, and stored procedures, the analysis explores **salary trends, remote work, employment patterns, geographic differences, experience levels, and career opportunities**.

The project provides a practical example of how SQL-based data analysis can support **business decision-making, workforce planning, compensation strategy, and career analysis**.

---

## 👩‍💻 Author

**Damini Anil Gadpal**

**Data Analytics / Data Science Learner**

Skills demonstrated in this project:

* SQL
* Data Analysis
* Data Cleaning
* Business Intelligence
* Statistical Thinking
* Problem Solving
* Business Insight Generation
