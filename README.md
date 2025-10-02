# Credit Card BI Dashboards

Interactive Business Intelligence dashboards for credit card transactions & customer analytics using PostgreSQL and Power BI.

---

## 🧾 Table of Contents

- [Project Overview](#project-overview)  
- [Features / Insights](#features--insights)  
- [Tech Stack](#tech-stack)  
- [Setup & Install](#setup--install)  
- [How to Push to GitHub](#how-to-push-to-github)  
- [Usage](#usage)  
- [Screenshots](#screenshots)  
- [Future Improvements](#future-improvements)  
- [Author](#author)  

---

## Project Overview

This project demonstrates how to build dashboards for credit card data, showing trends, revenue segmentation, customer demographics, and transaction behavior. The data is stored in PostgreSQL, visualized in Power BI, and surfaced with filters & slicers for interactivity.

---

## Features / Insights

- Revenue & transaction metrics by quarter & card category  
- Revenue by customer job, education, income, etc.  
- Transaction channel analysis (swipe, chip, online)  
- Time series analysis by week / date  
- Customer demographics & segmentation  

---

## Tech Stack

| Component        | Tool / Technology       |
|------------------|--------------------------|
| Data Storage      | PostgreSQL (via pgAdmin) |
| Data Import        | CSV → PostgreSQL (COPY)   |
| Visualization       | Power BI                   |
| Others (optional) | Python / ETL scripts (if used) |

---

## Setup & Install (Local)

Follow these steps to get a copy of the project running locally.

1. **Install PostgreSQL & pgAdmin**  
   Download and install from [postgresql.org](https://www.postgresql.org) (choose version compatible with your OS).  

2. **Create Database & Tables**  
   ```sql
   CREATE DATABASE ccdb;
   \c ccdb

   -- Example table structure (adjust columns as your project uses)
   CREATE TABLE cc_detail (
     id SERIAL PRIMARY KEY,
     week_start_date DATE,
     revenue BIGINT,
     total_trans_amt BIGINT,
     interest_earned BIGINT,
     card_category VARCHAR
     -- add other columns…
   );
   CREATE TABLE cust_detail (
     id SERIAL PRIMARY KEY,
     customer_id INT,
     income BIGINT,
     education_level VARCHAR,
     job VARCHAR
     -- and so on…
   );
   
Import CSV data
Set date style if your CSV uses DD-MM-YYYY:

SET datestyle = 'DMY';


Then run:

COPY cc_detail
  FROM 'D:/Credit Card BI Project/cc_add.csv'
  DELIMITER ','
  CSV HEADER;

COPY cust_detail
  FROM 'D:/Credit Card BI Project/cust_add.csv'
  DELIMITER ','
  CSV HEADER;


Connect Power BI to PostgreSQL

In Power BI, choose Get Data → PostgreSQL database

Enter server name (e.g. localhost) and database name (ccdb)

Import the tables and build visuals / dashboards