# Zepto Dataset Documentation

## Overview

This folder contains the raw product dataset used for the Zepto SQL Data Analysis project.

The dataset represents product-level information and supports analysis of pricing, discounts, stock availability, product categories, and inventory quantities.

## Dataset Profile

- **Total records:** 3,732
- **Total columns:** 9
- **File format:** CSV

## Column Descriptions

| Column | Description |
|---|---|
| `Category` | Product category |
| `name` | Product name |
| `mrp` | Maximum Retail Price |
| `discountPercent` | Discount percentage offered |
| `availableQuantity` | Available inventory quantity |
| `discountedSellingPrice` | Selling price after discount |
| `weightInGms` | Product weight in grams |
| `outOfStock` | Stock availability indicator |
| `quantity` | Quantity field supplied in the source dataset |

## Data Types

Recommended data types for the SQL table:

| Column | Suggested data type |
|---|---|
| `sku_id` | Auto-incrementing primary key |
| `Category` | VARCHAR |
| `name` | VARCHAR |
| `mrp` | DECIMAL |
| `discountPercent` | DECIMAL |
| `availableQuantity` | INTEGER |
| `discountedSellingPrice` | DECIMAL |
| `weightInGms` | INTEGER |
| `outOfStock` | BOOLEAN |
| `quantity` | INTEGER |

The `sku_id` column is generated when records are inserted into the SQL table; it is not one of the nine columns in the original CSV.

