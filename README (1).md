# AdventureWorks Sales Dashboard — Power BI

An end-to-end business intelligence project built with Power BI, analyzing 2.5 years of global bike company sales data across 6 countries, 4 product categories, and 18,000+ customers.

---

### Executive Overview
<img width="1278" height="721" alt="image" src="https://github.com/user-attachments/assets/6f24e489-95bf-4ce9-8974-f18a15774ac4" />


### Regional Sales Performance
<img width="1279" height="715" alt="image" src="https://github.com/user-attachments/assets/9f07eb1b-7bb4-4e69-81ea-91ed01e061bd" />


### Product Performance
<img width="1276" height="717" alt="image" src="https://github.com/user-attachments/assets/a7ef60ea-e457-4dbe-8aac-61925e818fd6" />


### Customer Insights
<img width="1277" height="715" alt="image" src="https://github.com/user-attachments/assets/51ef5f47-6df3-40cc-b77c-70fd5fa9f7b8" />


---

## Key Metrics

| Metric | Value |
|--------|-------|
| Total Revenue | $24.91M |
| Total Profit | $10.46M |
| Profit Margin | 42.0% |
| Total Orders | 56,046 |
| Total Customers | 18,151 |
| Total Returns | 1,828 |
| Date Range | Jan 2020 – Jun 2022 |

---

## Dashboard Pages

### 1. Executive Overview
High-level KPI summary with:
- Monthly revenue trend by year (2020, 2021, 2022)
- Top 5 countries by revenue (US $7.9M, Australia $7.4M leading)
- Top products by revenue (Road Bikes $11.3M, Mountain Bikes $8.6M)
- Year-over-year revenue comparison

### 2. Regional Sales Performance
Geographic breakdown including:
- Revenue by continent (North America $9.7M, Europe $7.8M, Pacific $7.4M)
- Interactive world map with revenue bubbles by country
- Drill-down table: continent → region → product category
- Return rate analysis by region (avg 2.17%)

### 3. Product Performance
Product-level analysis:
- Return rate by subcategory (Shorts highest at 4.24%)
- Top products by return rate (Road-650 Red at 11.76%)
- Full category hierarchy: Bikes / Accessories / Clothing / Components
- Average order value, total quantity, and total returns per product

### 4. Customer Insights
Customer segmentation:
- Top 20 customers by revenue (Jordan Turner leading at $15.57K)
- Revenue split by marital status (Single 51.78%, Married 48.22%)
- Revenue by gender (Male 50.23%, Female 49.14%)
- Occupation × Education cross-analysis matrix

---

## Data Model

The report uses a star schema with 1 fact table and 6 dimension tables:

```
Sales Data (fact)
├── Customer Lookup      — CustomerKey
├── Product Lookup       — ProductKey
│   ├── Product Subcategories — ProductSubcategoryKey
│   └── Product Categories    — ProductCategoryKey
├── Territory Lookup     — TerritoryKey
└── Calendar Lookup      — OrderDate
```

Returns Data is a secondary fact table linked via `ProductKey` and `TerritoryKey`.

---

## Dataset

**Source:** [AdventureWorks — Maven Analytics](https://www.mavenanalytics.io/)

| File | Rows | Description |
|------|------|-------------|
| AdventureWorks Sales Data 2020.csv | 2,630 | Transactional sales records |
| AdventureWorks Sales Data 2021.csv | 23,935 | Transactional sales records |
| AdventureWorks Sales Data 2022.csv | 29,481 | Transactional sales records |
| AdventureWorks Customer Lookup.csv | 18,154 | Customer demographics |
| AdventureWorks Product Lookup.csv | 293 | Product details and pricing |
| AdventureWorks Product Subcategories Lookup.csv | 37 | Subcategory hierarchy |
| AdventureWorks Product Categories Lookup.csv | 4 | Top-level categories |
| AdventureWorks Territory Lookup.csv | 10 | Region, country, continent |
| AdventureWorks Returns Data.csv | 1,809 | Return transactions |
| AdventureWorks Calendar Lookup.csv | 912 | Date dimension table |

**Countries covered:** United States, Canada, Australia, United Kingdom, France, Germany

---

## Tools & Techniques

| Area | Details |
|------|---------|
| Tool | Power BI Desktop |
| Data modeling | Star schema, relationships via primary/foreign keys |
| Calculations | DAX measures (revenue, profit, return rate, YoY growth) |
| Data prep | Power Query (type casting, column renaming, table merging) |
| Visuals | Line chart, bar chart, donut chart, map, matrix table, KPI cards |

---

## DAX Measures (examples)

```dax
Total Revenue = SUMX(Sales, Sales[OrderQuantity] * RELATED(Products[ProductPrice]))

Total Profit = [Total Revenue] - SUMX(Sales, Sales[OrderQuantity] * RELATED(Products[ProductCost]))

Profit Margin % = DIVIDE([Total Profit], [Total Revenue])

Return Rate % = DIVIDE([Total Returns], [Total Orders])
```

---

## Project Structure

```
adventureworks-dashboard/
│
├── screenshots/
│   ├── 01_executive_overview.png
│   ├── 02_regional_sales.png
│   ├── 03_product_performance.png
│   └── 04_customer_insights.png
│
└── README.md
```

---

## Key Insights

- Revenue grew from **$2.5M (2020)** to **$9.7M (2022)**, nearly 4x growth in 2.5 years
- **Road Bikes** alone generate 45% of total revenue ($11.3M out of $24.9M)
- **Australia** punches above its weight — comparable revenue to the US despite smaller market
- **Shorts** have the highest return rate (4.24%) among subcategories — a potential quality signal
- Customer base is nearly evenly split by gender and marital status — broad market appeal
- The **Southwest US region** is the single largest revenue region at $4.8M

Loyiha [ https://github.com/Adurasulov-data ] tomonidan tayyorlangan.
