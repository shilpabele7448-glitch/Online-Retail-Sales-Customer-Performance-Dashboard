# Online Retail Sales & Customer Performance Dashboard

## Project Overview

This project analyzes online retail transaction data using **Microsoft Power BI** to understand sales performance, customer purchasing behavior, product performance, returns, cancellations, and geographic sales trends.

The project transforms raw transaction data into an interactive dashboard containing KPIs, charts, filters, and business insights that can support data-driven reporting and decision-making.

---

## Business Objective

The main objective of this project is to analyze online retail transactions and answer important business questions such as:

- How are sales performing over time?
- What is the average order value?
- How many orders and customers are involved?
- What is the cancellation rate?
- Which products have the highest sales volume?
- Which products have the highest returned quantities?
- Which customers place the most orders?
- Which countries contribute the most sales?
- How do sales and cancellation patterns change over time?

---

## Dataset

**Dataset:** UCI Online Retail II

**Business Domain:** UK Online Retail / E-commerce

**Period:** 2009–2011

The dataset contains transaction-level information including:

- Invoice
- Stock Code
- Product Description
- Quantity
- Invoice Date
- Price
- Customer ID
- Country

The original dataset was divided into two yearly worksheets:

- `Year 2009-2010`
- `Year 2010-2011`

The two datasets were combined in Power Query for analysis.

> The original dataset is not included in this repository because of its size and dataset distribution considerations.

---

## Tools & Technologies

### Tools

- Microsoft Power BI
- Power Query
- DAX

### Skills Demonstrated

- Data Cleaning
- Data Transformation
- Data Quality Validation
- Data Modeling
- KPI Development
- DAX
- Sales Analysis
- Customer Analysis
- Product Analysis
- Return Analysis
- Cancellation Analysis
- Time-Series Analysis
- Geographic Analysis
- Data Visualization
- Dashboard Design

---

# Data Preparation & Cleaning

The original dataset contained two worksheets covering different periods:

- Year 2009–2010
- Year 2010–2011

Both datasets were combined using **Append Queries** in Power Query to create a single analysis table containing approximately **1,067,371 transaction rows**.

## Data Quality Checks

Column profiling was performed in Power Query to identify valid, empty, and erroneous values.

Key observations:

- Invoice contained valid values.
- StockCode contained valid values.
- Quantity contained valid values.
- InvoiceDate contained valid values.
- Price contained valid values.
- Country contained valid values.
- Description contained a small number of missing/error values.
- Customer ID contained approximately **23% missing values**.

Missing Description records were removed before the final analysis.

Customer ID was converted from a numeric data type to **Text** so that it could be treated as a customer identifier rather than a numerical measure.

---

## Data Transformations

The following transformations were performed in Power Query:

### 1. Append Yearly Data

The two yearly worksheets were appended into a single table named:

`Online_Retail`

### 2. Transaction Status

A new column called `Transaction_Status` was created.

Invoice numbers beginning with `C` were classified as:

`Cancelled`

Other invoices were classified as:

`Completed`

The classification produced:

- Completed transaction rows: **1,047,877**
- Cancelled transaction rows: **19,494**

### 3. Sales Amount

A calculated column called `Sales_Amount` was created using:

```text
Quantity × Price