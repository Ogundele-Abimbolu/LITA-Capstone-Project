# LITA-Capstone-Project
This project analyzes the sales performance data of a retail store to uncover insights on top products, regional performance, and monthly sales trends. The goal of this analysis is to assist decision-makers in making informed business choices. The insights are visualized in an interactive Power BI dashboard.

## Table of Contents
1. Project Overview
2. Data Analysis
   * Excel Analysis
   * SQL Analysis
3. Power BI Dashboard
4. Key Insights and Recommendations
5. Repository Structure
6. How to View the Dashboard

## Project Overview
This project is part of the LITA Capstone, where we aim to extract meaningful insights from sales data using Excel, SQL, and Power BI. The insights are expected to support business decisions by identifying trends, top-selling products, and regional sales performance.


## Tools Used:
* Excel for data exploration
* SQL for querying and analysis
* Power BI for interactive data visualization


# Data Analysis
## Excel Analysis
Initial data exploration and calculations were performed in Excel. Key steps included:

* ## Pivot Tables:
     * Created pivot tabled to display:
       * Total Sales by Product: To identify high-performing products.
       * Sales by Region: To determine regional demand.
       * Monthly Sales Trends: To identify seasonality in sales.
* ## Calculations:
     * Used Excel formulas to calculate metrics such as:
        * Average Sales per Product: Provides a benchmark for product performance.
        * Total Revenue by Region: To see which regions contributed most to revenue.
* ## Additional Reports:
     * Analyzed top-selling products using filtering options in the pivot tables.


# SQL Analysis
Further insights were gathered using SQL queries to address specific business questions. Here are the queries used and the insights they provided:

1. Total Sales by Product Category:
   
```SQL
SELECT product_category, SUM(sales_amount) AS total_sales
FROM sales_data
GROUP BY product_category;

   
   
   
