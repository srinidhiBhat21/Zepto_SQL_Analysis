# Zepto SQL Analysis

## Overview

This folder contains the SQL script used to explore, clean, and analyze Zepto product data.

The queries focus on product pricing, discount percentages, stock availability, category-level inventory estimates, and product weight analysis.

## Database Setup

The SQL script uses a database named `zepto` and creates a table named `zepto`.

The table contains the following fields:

- `sku_id`
- `category`
- `name`
- `mrp`
- `discountPercent`
- `availableQuantity`
- `discountedSellingPrice`
- `weightInGms`
- `outOfStock`
- `quantity`

The `sku_id` field is generated as an auto-incrementing primary key.

## Query Sections

### 1. Data Exploration

The script includes queries to:

- Count total records
- View sample data
- Check for missing values
- Identify distinct product categories
- Count products by stock availability
- Identify repeated product names

### 2. Data Cleaning

The script investigates zero-price records, removes a record with zero MRP, and converts MRP and discounted selling prices from paise to rupees.

These transformations should be applied only after confirming the source price units.

### 3. Business Questions

| No. | Business question | SQL concepts 
| 1 | Find the top 10 products by discount percentage | `DISTINCT`, `ORDER BY`, `LIMIT` |
| 2 | Find high-MRP products that are out of stock | `WHERE`, filtering, sorting |
| 3 | Estimate inventory value for each category | `SUM()`, `GROUP BY` |
| 4 | Find products with MRP above ₹500 and discount below 10% | Multiple `WHERE` conditions |
| 5 | Find the five categories with the highest average discount | `AVG()`, `ROUND()`, `GROUP BY` |
| 6 | Calculate price per gram for products weighing at least 100 grams | Calculations, `ROUND()`, sorting |
| 7 | Categorize products as Low, Medium, or Bulk by weight | `CASE` |
| 8 | Calculate total inventory weight by category | `SUM()`, `GROUP BY` |

## Example Queries

### Top 10 Products by Discount

```sql
SELECT DISTINCT name, mrp, discountPercent
FROM zepto
ORDER BY discountPercent DESC
LIMIT 10;
```

### High-MRP Products That Are Out of Stock

```sql
SELECT DISTINCT name, mrp
FROM zepto
WHERE outOfStock = TRUE
  AND mrp > 300
ORDER BY mrp DESC;
```

### Estimated Inventory Value by Category

```sql
SELECT
    category,
    SUM(discountedSellingPrice * availableQuantity)
        AS estimated_inventory_value
FROM zepto
GROUP BY category
ORDER BY estimated_inventory_value DESC;
```

### Categories with the Highest Average Discount

```sql
SELECT
    category,
    ROUND(AVG(discountPercent), 2) AS avg_discount
FROM zepto
GROUP BY category
ORDER BY avg_discount DESC
LIMIT 5;
```

### Price per Gram

```sql
SELECT DISTINCT
    name,
    weightInGms,
    discountedSellingPrice,
    ROUND(
        discountedSellingPrice / weightInGms,
        2
    ) AS price_per_gram
FROM zepto
WHERE weightInGms >= 100
ORDER BY price_per_gram;
```

### Product Weight Classification

```sql
SELECT DISTINCT
    name,
    weightInGms,
    CASE
        WHEN weightInGms < 1000 THEN 'Low'
        WHEN weightInGms < 5000 THEN 'Medium'
        ELSE 'Bulk'
    END AS weight_category
FROM zepto;
```

## SQL Skills Demonstrated

- Data exploration and validation
- Data cleaning with `UPDATE` and `DELETE`
- Filtering with `WHERE`
- Grouping with `GROUP BY`
- Filtering grouped results with `HAVING`
- Aggregations using `COUNT()`, `SUM()`, and `AVG()`
- Sorting and limiting query results
- Conditional logic using `CASE`
- Calculating derived metrics
- Answering practical business questions

## Execution Notes

1. Create or select the `zepto` database.
2. Create the table using the schema in the SQL script.
3. Import `zepto_main.csv` into the table, mapping the CSV fields to the matching columns and allowing `sku_id` to generate automatically.
4. Execute the data exploration queries.
5. Review the data cleaning queries before executing any destructive statements.
6. Run the business analysis queries.
7. Validate the output against the source data.

The supplied SQL file uses MySQL-style database commands and data types. If using a different database system, adjust the syntax accordingly.

