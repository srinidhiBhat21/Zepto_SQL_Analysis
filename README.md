# Zepto Data Analysis using SQL

## Project Overview

This project focuses on analyzing Zepto product and inventory data using SQL to uncover insights related to product pricing, discounts, stock availability, product categories, and inventory value.

The objective is to transform raw product data into meaningful business insights by performing data exploration, data cleaning, and SQL-based analysis to answer practical business questions.


## Project Objectives

- Explore product data and understand the dataset structure.
- Identify missing values and duplicate product names.
- Clean product pricing data and handle invalid price records.
- Analyze product availability and out-of-stock products.
- Identify products offering the highest discounts.
- Estimate inventory value across product categories.
- Compare product pricing and discounts.
- Calculate price per gram to compare product value.
- Categorize products based on weight.
- Answer business questions using SQL queries.

## Tools and Technologies

- **SQL** — data exploration, cleaning, aggregation, and business analysis
- **MySQL** — relational database management
- **CSV** — source dataset

## Dataset Overview

The project uses a Zepto product dataset containing **3,732 rows and 9 columns**.

The dataset includes product categories, product names, MRP, discount percentages, available quantities, discounted selling prices, product weights, stock status, and quantity information.


## Data Exploration and Cleaning

The following operations were performed in SQL:

- Inspected the dataset and retrieved sample records.
- Counted the total number of records.
- Checked for missing values across relevant columns.
- Identified distinct product categories.
- Analyzed in-stock and out-of-stock products.
- Identified product names appearing multiple times.
- Investigated products with zero MRP or selling price.
- Removed a product record with zero MRP.
- Converted MRP and discounted selling prices from paise to rupees.

## Business Questions Solved

1. Which products offer the highest discount percentages?
2. Which high-MRP products are out of stock?
3. What is the estimated inventory value for each product category?
4. Which products have an MRP greater than ₹500 and a discount below 10%?
5. Which five categories have the highest average discount percentage?
6. What is the price per gram of products weighing at least 100 grams?
7. How can products be categorized into Low, Medium, and Bulk weight groups?
8. What is the total inventory weight for each category?

## SQL Concepts Used

- `SELECT` and `DISTINCT`
- `WHERE` and filtering conditions
- `ORDER BY` and `LIMIT`
- `GROUP BY` and `HAVING`
- Aggregate functions such as `COUNT()`, `SUM()`, and `AVG()`
- `ROUND()` for numerical formatting
- `CASE` statements for conditional categorization
- `UPDATE` and `DELETE` for data cleaning
- Table creation and database operations

## Key Learnings

- Exploring and validating raw datasets using SQL
- Identifying data quality issues
- Cleaning price data before analysis
- Applying aggregation and filtering to answer business questions
- Comparing discounts and product value
- Analyzing stock availability and inventory
- Translating business problems into SQL queries

## Important Notes

The estimated category value is calculated using discounted selling price multiplied by available quantity. It represents an inventory-value estimate based on the available quantity field, not verified sales revenue.

Product names appearing multiple times may represent different SKUs or product variants, so duplicate names should not automatically be treated as duplicate records.

The dataset's currency conversion assumes the original price fields are stored in paise. This assumption should be validated against the source data.

## Author

**Srinidhi Bhat**

Aspiring Data Analyst | SQL | Python | Excel | Power BI

Project 05/50 — 50 Data Analysis Projects
