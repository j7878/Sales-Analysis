# Enhancing Sales Insights for C&G

## Table of Contents
- [Project Overview](#project-overview)
- [Tools](#tools)
- [Data cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Model star schema with Tableau](#data-model-star-schema-with-tableau)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)

### Project Overview

Amid challenges faced by C&G, Sales Director Kash Kent struggles with obtaining accurate performance insights and faces communication biases from regional managers. This project aims to overcome these hurdles by streamlining data analysis processes and improving transparency. By transitioning from complex Excel files to advanced analytics techniques, the project seeks to empower decision-making and drive effective sales strategies.

### Tools

- Excel - Data Cleaning
- MYSQL - Data Analysis
- Tableau - Creating reports


  ### Data cleaning and Preparation

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

### Data Model star schema with Tableau

Utilizing ETL (Extract, Transform, Load) techniques, raw data from MySQL databases underwent a comprehensive transformation process. 

<img width="474" alt="Data model " src="https://github.com/j7878/Sales-Analysis/assets/58298723/5587b994-db41-4d7f-90ca-2848233fb1b0">

Once the transformation process was complete, the transformed data was loaded into Tableau, a powerful data visualization tool. Leveraging Tableau's interactive features, an intuitive dashboard was created to visualize key insights derived from the integrated data model. The dashboard provided stakeholders with a user-friendly interface to explore and analyze data dynamically, facilitating informed decision-making and driving business insights

### Results and Findings

The analysis resukts are summarized as follows:
1. Identified key geographical areas for targeted sales efforts based on revenue breakdown by cities.
2. Analyzed trends and patterns over time to understand sales performance fluctuations by examining revenue breakdown by years and months.
3. Prioritized customer relationship management efforts by identifying the top five customers based on sales quantity and revenue.
4. Informed product development and marketing strategies by identifying the top five products by revenue.

### Recommendations 

Based on the analysis, we recommend the following actions: 
- Focus sales efforts on key contributing cities to maximize returns.
- Adapt sales strategies based on identified trends and patterns over time, considering seasonal variations.
- Prioritize top customers for personalized attention and service to strengthen relationships.
- Invest resources in promoting and developing top-performing products, tailoring marketing campaigns accordingly.

  ### Limitations

  - Analysis relies on the accuracy and completeness of available sales data, which may introduce biases or errors.
  - Scope primarily focuses on sales data, potentially overlooking other factors influencing business performance.
  - Dashboard effectiveness depends on user familiarity with Tableau and data interpretation skills.
  - Business environment dynamics may render insights less relevant over time, necessitating regular updates and strategy adjustments.



  
