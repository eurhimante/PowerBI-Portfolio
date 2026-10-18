# 01 — Business Performance Dashboard | Power BI

[← Back to Power BI Portfolio](../README.md)

**An interactive business intelligence report for monitoring sales, profit and profitability across countries, products, customer segments and time.**

**Tools:** Power BI Desktop · Power Query · DAX · Excel  
**Dataset:** Microsoft Financial Sample (demonstration data)  
**Report:** [`BusinessPerformance.pbix`](BusinessPerformance.pbix)

![Executive Overview dashboard](images/Executive%20Overview.png)

## 1. Project overview

Business stakeholders need a consolidated view of commercial performance to understand **where revenue comes from, which activities generate profit, and how results change over time**. This project transforms an Excel-based financial dataset into a four-page interactive Power BI report.

The dashboard is designed for exploratory decision support: users can start with company-wide indicators, then investigate specific countries, segments and products.

### Business questions

- How do sales and profit evolve over time? Are there recurring peaks or slow periods?
- Which countries contribute the most to sales?
- Which products lead in revenue, and how does their profitability compare?
- Which customer segments contribute most to profit?
- How do current-period results compare with the previous year?

## 2. Dataset and scope

**Source:** [`Financial Sample.xlsx`](data/Financial%20Sample.xlsx), Microsoft's publicly available financial sample dataset.

The source includes commercial transactions and attributes such as country, product, customer segment, date, sales and profit. It is used here as a **learning and demonstration dataset**, not as real-time financial information.

**Dimensions used for analysis:**

| Dimension | Analytical purpose |
|---|---|
| Date | Monthly evolution and year-over-year comparisons |
| Country | Geographic sales and profitability comparisons |
| Product | Product performance and contribution |
| Segment | Customer segment performance |

## 3. Data preparation and modelling

The workbook was imported into Power BI and prepared using **Power Query**. The workflow included:

1. Checking data types, especially dates and numeric financial fields.
2. Reviewing data consistency and potential quality issues.
3. Renaming tables and columns for easier interpretation.
4. Creating a dedicated date dimension to support time-based analysis.
5. Organising the model around a sales fact table linked to the date dimension.

### Simplified data model

```text
Dim_Date
   │  (1 → *)
   ▼
Fact_Sales
```

The commercial attributes (country, product and segment) are available for filtering and breakdowns in the sales data. The diagram is **a simplified representation**, not a claim of a fully normalised dimensional model.

## 4. KPIs and analytical features

The report combines core financial indicators with breakdowns and time comparisons:

| Indicator | Purpose |
|---|---|
| Total Sales | Monitor overall sales volume in monetary terms |
| Total Profit | Measure aggregate profitability in monetary terms |
| Profit Margin | Compare profit relative to sales |
| Sales Growth % | Compare sales across periods |
| Sales by Country / Product | Identify key revenue contributors |
| Profit by Segment | Identify segments contributing most to profit |

**Illustration:** In the unfiltered Executive Overview screenshot, the report displays approximately **$118.73M in sales**, **$16.89M in profit** and a **14.23% profit margin**. These figures describe the sample and depend on the active report filters.

### Interactivity

- Slicers for **customer segment**, **country** and **year**.
- Cross-filtering between KPI cards and charts.
- Navigation between four report pages, from a high-level overview to detailed analysis.
- Time-series visualisation to investigate changes in sales over the reporting period.

## 5. Dashboard walkthrough

### Executive Overview

A compact view of overall sales, profit, profit margin and growth, alongside trends and top contributors by country, segment and product.

![Executive Overview](images/Executive%20Overview.png)

### Sales Analysis

A closer look at sales distribution and evolution over time, designed to compare products, markets and periods.

![Sales Analysis](images/Sales%20Analysis.png)

### Profitability Analysis

A profit-focused page for distinguishing high-revenue areas from the most profitable countries, products and segments.

![Profitability Analysis](images/Profitability%20Analysis.png)

### Product Details

A product-level exploration of performance to identify leading products and compare their contributions.

![Product Details](images/Product%20Details.png)

## 6. Key findings

The sample report highlights several patterns:

- **Geographic contribution:** The United States and Canada are among the largest sales contributors.
- **Customer segments:** Government is the leading segment in total profit.
- **Product mix:** Paseo generates the highest sales in the dataset.
- **Profitability:** Germany shows the strongest profit margin among the countries analysed.
- **Seasonality:** Sales show a notable peak around October in the period displayed.

These findings are **descriptive observations from the sample dataset**. They are not forecasts, causal conclusions or statements about current business conditions.

## 7. Skills demonstrated

- **Power Query:** importing and preparing Excel data, validating types and organising tables.
- **Data modelling:** relating a date dimension to transactional sales data.
- **DAX:** creating financial KPIs, profitability metrics and time-based comparisons.
- **Power BI reporting:** building interactive slicers, charts, KPI cards and multi-page navigation.
- **Business analysis:** translating commercial questions into readable indicators and actionable comparisons.
- **Data storytelling:** moving from an executive summary to more granular exploration.

## 8. Reproduce the report

1. Download or clone this repository.
2. Open [`BusinessPerformance.pbix`](BusinessPerformance.pbix) using **Power BI Desktop**.
3. If Power BI cannot find the original data source, update its path to [`data/Financial Sample.xlsx`](data/Financial%20Sample.xlsx) in the data source settings.
4. Refresh the data and explore the report using its filters and pages.

> **Limitations:** The report uses historical demonstration data. The indicators reflect the dataset and current filter context; the analysis is intended to demonstrate BI skills rather than to support actual financial decisions.

