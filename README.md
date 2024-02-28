# Enhancing Sales Insights for C&G

### Project Overview

Amid challenges faced by C&G, Sales Director Kash Kent struggles with obtaining accurate performance insights and faces communication biases from regional managers. This project aims to overcome these hurdles by streamlining data analysis processes and improving transparency. By transitioning from complex Excel files to advanced analytics techniques, the project seeks to empower decision-making and drive effective sales strategies.

### Tools

- Excel - Data Cleaning
- MYSQL - Data Analysis
- Tableau - Creating reports


  ### Data cleaning/Preparation

  in the initial data preparation phase, we performed the following tasks:
  1. Data loadiing and inspection
  2. Handling missing values.
  3. Data cleaning and formatting.
 
  ### Exploratory Data Analysis

  EDA involved exploring the sales data to answer key questions, such as:

 - Show total number of customers
  -Show transactions for Chennai market (market code for chennai is Mark001
  - Show distinct product codes that were sold in chennai
  - Show transactions where currency is US dollars
  - Show transactions in 2020 join by date table
  - Show total revenue in year 2020
  - show revenue in year 2020, Janaury Month

    ### Data Analysis

  ```sql
  
 SELECT count(*) FROM sales.customers;

SELECT *
 FROM sales.transactions
 where market_code='Mark001';

 SELECT distinct product_code 
 FROM sales.transactions
 where market_code='Mark001';

 SELECT *
 from sales.transactions
 where currency='USD';

SELECT transactions.*, date.*
FROM sales.transactions
INNER JOIN sales.date 
ON transactions.order_date = sales.date.date
WHERE sales.date.year = 2020;

SELECT SUM(transactions.sales_amount) AS Total_Revenue_2020
FROM sales.transactions
INNER JOIN sales.date 
ON transactions.order_date = sales.date.date
WHERE sales.date.year = 2020;

SELECT SUM(transactions.sales_amount) AS Total_Revenue_January_2020
FROM sales.transactions
INNER JOIN sales.date 
ON transactions.order_date = sales.date.date
WHERE sales.date.year = 2020
AND sales.date.month_name = 'January'
AND (transactions.currency = 'INR' OR transactions.currency = 'USD');

 ```
### Data Model 

  
