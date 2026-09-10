# Business Performance Dashboard

## Project Overview

This project analyzes business performance using Power BI.

The objective is to provide an interactive dashboard allowing stakeholders to analyze sales, profit, profitability and performance across countries, products and customer segments.

---

## Business Questions

- How are sales evolving over time?
- Which countries generate the most revenue?
- Which products are the most profitable?
- Which customer segments generate the most profit?
- How does performance compare with the previous year?

---

## Tools

- Power BI Desktop
- Power Query
- DAX
- Excel

---

## Data Preparation

The dataset was imported from an Excel workbook.

Data preparation included:

- Data type validation
- Data quality checks
- Table renaming
- Date table creation

---

## Data Model

The report uses a simple star schema:

Dim_Date
    ↓
Fact_Sales

---


```DAX
Total Sales =
SUM(Fact_Sales[Sales])
