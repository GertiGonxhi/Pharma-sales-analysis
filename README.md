# Pharmaceutical Sales Analysis

A MySQL and Google Data Studio project built on 6 years of real daily sales data from a pharmacy.

## Project Overview

I wanted to answer a simple question: what does a pharmacy actually sell, when does it sell the most, and what can be improved?

To figure that out I built a MySQL database with 5 tables, wrote 10 SQL queries to dig into the data, and put everything into a 3-page dashboard in Google Data Studio.

## Project Structure

```
pharma-sales-analysis/
│
├── sql/
│   └── pharma_analysis_documented.sql
│
├── dashboard/
│   └── screenshots/
│       ├── page1_sales_overview.png
│       ├── page2_patterns_insights.png
│       └── page3_recommendations.png
│
└── README.md
```

## Database Schema

The database has 5 tables:

| Table | Description |
|---|---|
| sales_daily | Main table — one row per day, one column per medicine |
| sales_hourly | Same structure but broken down by hour |
| sales_weekly | Weekly totals |
| sales_monthly | Monthly totals |
| drug_categories | Lookup table that maps ATC codes to medicine names |

8 medicines are tracked:

| Code | Medicine | Category |
|---|---|---|
| N02BE | Paracetamol | Analgesic |
| M01AB | Ibuprofen | Anti-inflammatory |
| M01AE | Diclofenac | Anti-inflammatory |
| N02BA | Aspirin | Analgesic |
| N05B | Diazepam | Anxiolytic |
| N05C | Nitrazepam | Sedative |
| R03 | Salbutamol | Respiratory |
| R06 | Loratadine | Antihistamine |

## SQL Queries

10 questions, each answered with a separate query:

| # | Question | Technique used |
|---|---|---|
| 1 | Which medicines sell the most? | UNION ALL unpivot + JOIN |
| 2 | How does revenue trend month by month? | DATE_FORMAT + GROUP BY |
| 3 | Which season drives the highest sales? | CASE statement + AVG |
| 4 | How has revenue grown year over year? | GROUP BY Year + SUM |
| 5 | Which day of the week performs best? | GROUP BY Weekday + AVG |
| 6 | What time of day are sales highest? | Hourly table + GROUP BY Hour |
| 7 | How do we rate each month's performance? | CASE thresholds on aggregates |
| 8 | Do weekends outperform weekdays? | CASE grouping + COUNT |
| 9 | What is the cumulative revenue over time? | Window function SUM() OVER |
| 10 | Do high Paracetamol days lift all sales? | CASE bucketing + correlation |

Every query has comments explaining what I was trying to find out, how I approached it, and what the result means. See [sql/pharma_analysis_documented.sql](sql/pharma_analysis_documented.sql)

## Dashboard

3 pages built in Google Data Studio.

### Page 1 — Sales Overview
Total sales by medicine, monthly revenue trend, and seasonal patterns.

![Sales Overview](dashboard/screenshots/page1_sales_overview.png)

### Page 2 — Patterns and Insights
Day-of-week breakdown, peak hours, and product mix.

![Patterns and Insights](dashboard/screenshots/page2_patterns_insights.png)

### Page 3 — Business Recommendations
Three recommendations based on what the data showed.

![Business Recommendations](dashboard/screenshots/page3_recommendations.png)

## Key Findings

| Finding | Detail |
|---|---|
| Top product | Paracetamol makes up around 50% of total revenue |
| Peak season | Winter — sales spike every October through January |
| Seasonal pattern | Loratadine peaks in Spring, lining up with allergy season |
| Best day | Saturday averages €65.67 vs €57.18 on Thursday |
| Anomaly | Revenue dropped 23% in 2017 compared to 2016 |
| Correlation | On high Paracetamol days, all other medicines tend to sell more too |

## Recommendations

| # | Recommendation | Why |
|---|---|---|
| 1 | Stock up on Paracetamol before winter | It drives 50% of revenue and spikes every October — ordering 30% extra in September avoids running out during peak months |
| 2 | Schedule more staff on Saturdays | Strongest revenue day by average — Thursday is the quietest, good day to reduce hours |
| 3 | Investigate the 2017 revenue drop | Revenue fell from €25,235 to €19,399 — a 23% drop. Finding the cause could help recover that lost ground |

## Tools Used

| Tool | Purpose |
|---|---|
| MySQL | Database design and all queries |
| MySQL Workbench | Schema design and EER diagram |
| Google Data Studio | Dashboard and visualizations |
| Excel | Initial data exploration |

## About

This project was built by me, Gerti Gonxhi as part of a personal portfolio to practice real-world data analysis, from building a database to creating a business dashboard.

📧 Email: Geerttsh@gmail.com
