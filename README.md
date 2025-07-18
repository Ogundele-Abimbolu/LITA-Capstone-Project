# LITA-Capstone-Project
This project analyses sales performance data from a retail store to uncover insights into top products, regional performance, and monthly sales trends. The goal of this analysis is to help decision-makers make informed business decisions. The insights are visualised in an interactive Power BI dashboard.

## Table of Contents
1. [Project Overview](#project-overview)
2. [ Data Analysis](#data-analysis)
   * [Excel Analysis](#excel-analysis)
   * [SQL Analysis](#sql-analysis)
3. [Power BI Dashboard](#power-bi-dashboard)
4. [Key Insights and Recommendations](key-insights-and-recommendations)
5. [Repository Structure](#repository-structure)
6. [How to View the Dashboard](#how-to-view-the-dashboard)

## Project Overview
This project is part of the LITA Capstone, where we aim to extract meaningful insights from sales data using Excel, SQL, and Power BI. The insights are expected to support business decisions by identifying trends, top-selling products, and regional sales performance.


## Tools Used:
* Excel for data exploration
* SQL for querying and analysis
* Power BI for interactive data visualisation


# Data Analysis
## Excel Analysis
Initial data exploration and calculations were performed in Excel. Key steps included:

* ### Pivot Tables:
     * Created a pivot table to display:
       * Total Sales by Product: To identify high-performing products.
       * Sales by Region: To determine regional demand.
       * Monthly Sales Trends: To identify seasonality in sales.
* ### Calculations:
     * Used Excel formulas to calculate metrics such as:
        * Average Sales per Product: Provides a benchmark for product performance.
        * Total Revenue by Region: To see which regions contributed most to revenue.
* ### Additional Reports:
     * Analysed top-selling products using filtering options in the pivot tables.


# SQL Analysis
Further insights were gathered using SQL queries to address specific business questions. Here are the queries used and the insights they provided:

1. **Total Sales by Product Category:**
   
```SQL
SELECT product_category, SUM(sales_amount) AS total_sales
FROM sales_data
GROUP BY product_category;
```
 * Insight: Helps in understanding which product categories generate the most revenue.

2. **Number of Sales Transactions in Each Region:**

```SQL
SELECT region, COUNT(*) AS transaction_count
FROM sales_data
GROUP BY region;
```
 * Insight: Shows the volume of sales across different regions, helping in resource allocation.

3. **Highest-Selling Product by Total Sales Value:**

```SQL
SELECT product, SUM(sales_amount) AS total_sales
FROM sales_data
GROUP BY product
ORDER BY total_sales DESC
LIMIT 1;  -- Or use TOP 1 for SQL Server
```
 * Insight: Identifies the single highest-performing product by sales value.

4. **Total Revenue per Product:**

```SQL
SELECT product, SUM(sales_amount) AS total_revenue
FROM sales_data
GROUP BY product;
```
 * Insight: Shows the revenue generated by each product.

5. **Monthly Sales Totals for the Current Year:**

```SQL
SELECT MONTH(sale_date) AS month, SUM(sales_amount) AS monthly_total
FROM sales_data
WHERE YEAR(sale_date) = YEAR(GETDATE())
GROUP BY MONTH(sale_date);
```
 * Insight: Highlights sales trends across months, useful for seasonal planning.

6. **Top 5 Customers by Purchase Amount:**
   
```SQL
SELECT customer_id, SUM(sales_amount) AS total_purchase
FROM sales_data
GROUP BY customer_id
ORDER BY total_purchase DESC
LIMIT 5;
```
 * Insight: Lists the top customers, aiding in targeted marketing efforts.

7. **Sales Percentage By Region:**

```SQL
WITH total_sales AS (
    SELECT SUM(sales_amount) AS grand_total
    FROM sales_data
)
SELECT region,
       SUM(sales_amount) AS region_sales,
       (SUM(sales_amount) / (SELECT grand_total FROM total_sales) * 100) AS sales_percentage
FROM sales_data
GROUP BY region;
```
 * Insight: Shows each region’s contribution to total sales, helping to focus marketing efforts.

8. **Products with No Sales in the Last Quarter:**

```SQL
SELECT product
FROM sales_data
WHERE sale_date < DATEADD(QUARTER, -1, GETDATE())
GROUP BY product
HAVING SUM(sales_amount) IS NULL OR SUM(sales_amount) = 0;
```
 * Insight: Identifies products with poor performance for potential review.


# Power BI Dashboard
The Power BI dashboard visualises the main findings, allowing stakeholders to interact with and explore the data.

* Sales Overview: Highlights total sales, total transactions, and average sales per product.
* Top Products: A visual summary of the top-selling products.
* Regional Breakdown: A map showing total sales by region, with transaction count and revenue details.
* Monthly Sales Trends: A line chart displaying sales over months to identify seasonal trends.
* Customer Insights: A breakdown of the top customers by purchase amount.

The dashboard includes filters and slicers for categories, regions, and date ranges, enabling users to analyse specific segments of the data.

![LITA CAPSTONE PROJECT 1 SUBMIT](https://github.com/user-attachments/assets/35a504b0-7975-4db9-8b9c-cd866ca67631)

![LITA CAPSTONE PROJECT II SUBMIT](https://github.com/user-attachments/assets/6e920b9b-f6f9-442d-b4db-6e1eb796ef37)

## Key Insights and Recommendations
Based on the analysis, here are the main takeaways and actionable recommendations:

- Top Products: Key products drive a significant portion of sales. Recommend optimising stock levels for these products.
- Regional Performance: Some regions contribute more to sales, suggesting focused marketing could enhance performance in lower-performing areas.
- Monthly Trends: Monthly trends reveal seasonal spikes, useful for inventory and marketing planning.
  
## Recommendations:

1. Increase inventory for top-selling products.
2. Launch targeted marketing campaigns in underperforming regions.
3. Plan inventory around identified peak sales months.
   
