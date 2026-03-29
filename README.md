Business Insights 360 - AtliQ Hardware

Company Overview
AtliQ Hardware is a fast-growing global electronics manufacturer that sells hardware products including PCs, keyboards, printers, monitors, and hard disks across India and international markets.

AtliQ Retailers → Ecommerce (Amazon, Croma) & Brick and Mortar (Sage, Novus)
AtliQ Direct → AtliQ Hardware Store & AtliQ Hardware Exclusive
AtliQ Distributors → Neptune 

All channels ultimately serve Final Consumers.

Problem Statement
AtliQ Hardware has been expanding rapidly across global markets. With this growth, the volume of data skyrocketed and Excel, the company's primary analytics tool, started breaking down:
Slow performance, Reports took hours to generate, File corruption risks, Data loss incidents, Collaboration issues, Teams couldn't work simultaneously, Row/column limits, Couldn't handle millions of records
The solution: Migrate to MySQL for data management and Power BI for visualization enabling real-time dashboards, advanced analytics, and data-driven decisions across Finance, Sales, Marketing, and Supply Chain.

Project Objective
Build an end-to-end Business Intelligence solution that gives AtliQ's top management a single source of truth — a 360° view of business performance across all departments, markets, customers, and products.

Tools & Technologies

| Tool | Purpose |
|---|---|
| **MySQL** | Database management, querying, stored procedures |
| **Power BI** | Data modeling, DAX, interactive dashboards |
| **Excel** | Pivot table reports, ad-hoc analysis |
| **DAX Studio** | Report optimization and performance tuning |

---

## SQL Work

### Key Concepts Applied
- Fiscal year conversion using `DATE_ADD` (AtliQ follows **Sep 1 – Aug 31** fiscal year)
- JOINs across `fact_sales_monthly`, `dim_customer`, `dim_product`, `fact_gross_price`
- Dynamic **User-Defined Functions**: `get_fiscal_year()`, `get_fiscal_quarter()`
- **Stored Procedures** to automate reusable reports (e.g., `get_market_badge` — classifies markets as Gold/Silver based on sales volume)

### Sample Queries Solved
- Product-wise sales report for Croma India (FY 2021) — Month, Product, Variant, Sold Qty, Gross Price per Item, Gross Price Total
- Yearly gross sales report for Croma India across FY 2018–2022
- Market badge classification: India → **Gold** (>5M units sold)

---

## Data Modeling

**Schema:** Hybrid (Star + Snowflake)

**Fact Tables:**
- `fact_sales_monthly`
- `fact_actual_estimates`
- `fact_gross_price`
- `post_invoice_deductions`
- `manufacturing_cost`
- `freight_cost`

**Dimension Tables:**
- `dim_customer`
- `dim_product`
- `dim_market`
- `dim_date`
- `NsGmTarget`
- `Operational_Expense`
- `fiscal_year`

All tables are connected via keys (`customer_code`, `product_code`, `market`, `fiscal_year`) with a dedicated **Date Table** for accurate time intelligence.

---

## Finance Logic (P&L Flow)

```
Gross Price
  → Pre Invoice Deductions
= Net Invoice Sales
  → Post Invoice Discounts (Promotional Offers + Placement Fees + Performance Rebate)
= Net Sales
  → COGS (Manufacturing Cost + Transport Cost + Other Cost)
= Gross Margin
= Gross Margin %
```

---

## Power BI Dashboard — Views

### Home View
Central navigation hub — users land here and navigate to any department view.
<img width="896" height="505" alt="image" src="https://github.com/user-attachments/assets/72702595-eee0-4eb0-8825-68f53534ded4" />

---

### Finance View
**Problem:** Financial data was scattered, making it hard to assess company health.  
**Solution:** Consolidated P&L statement with:
- Net Sales, Gross Margin %, Net Profit % KPI cards
- Year-over-Year (YoY) and vs. Target comparisons
- Profitability/Growth matrix by customer, product, and country
- Net Sales performance trend over time

<img width="898" height="507" alt="image" src="https://github.com/user-attachments/assets/e991a7ea-503b-47ec-b480-5bccd0f8bf42" />

---

### Sales View
**Problem:** Sales performance across customers was unclear.  
**Solution:** Customer-level analysis with:
- Net Sales & Gross Margin by customer
- Profitability/Growth matrix
- Performance vs. benchmark and targets

<img width="896" height="503" alt="image" src="https://github.com/user-attachments/assets/62b38371-a751-4134-aa0c-c65b94cc3739" />

---

### Marketing View
**Problem:** Marketing lacked product-level performance insight.  
**Solution:** Product performance analysis with:
- Net Sales, Gross Margin by product segment
- Segment-wise P&L YoY comparison (Accessories, Desktop, Networking, Notebook, Peripherals, Storage)

<img width="897" height="505" alt="image" src="https://github.com/user-attachments/assets/a72b3480-c8d9-4019-88b3-3d7b720a23d2" />

---

### Supply Chain View
**Problem:** Supply chain had no visibility into forecast accuracy or risk.  
**Solution:** Supply chain KPIs including:
- Forecast Accuracy %
- Net Error
- Risk profiles by product, segment, and customer

<img width="898" height="504" alt="image" src="https://github.com/user-attachments/assets/87c57807-6bb7-4545-bb32-e9f0c46fd9ba" />

---

## Performance Optimization (DAX Studio)

| Optimization | Result |
|---|---|
| Disabled unnecessary column loads | Reduced data model size |
| Applied query folding | Only required columns extracted from source |
| Replaced calculated columns with DAX measures | Faster refresh and load |
| Used DAX variables | Cleaner, more efficient calculations |
| Hybrid schema (Star + Snowflake) | Balanced flexibility and performance |
| Dedicated Date Table | Accurate time intelligence across all visuals |

---

## Repository Structure

```
 atliq-hardware-business-insights-360
 ┣  Excel/
 ┃ ┗ pivot_reports.xlsx
 ┃  SQL/
 ┃ ┣ croma_product_sales_report.sql
 ┃ ┣ fiscal_year_functions.sql
 ┃ ┣ stored_procedures.sql
 ┃ ┗ yearly_gross_sales.sql
 ┣ PowerBI/
 ┃ ┗ atliq_business_insights_360.pbix
 ┣ 📁 Screenshots/
 ┃ ┣ finance_view.png
 ┃ ┣ sales_view.png
 ┃ ┣ marketing_view.png
 ┃ ┣ supply_chain_view.png
 ┃ ┗ data_model.png
 ┗ README.md
```

---

## Live Report

https://www.novypro.com/project/project-360

---

## About

Built as an end-to-end business analytics project covering SQL, data modeling, DAX, and Power BI dashboard design, targeting real-world analytics roles.




ToolPurposeMySQLDatabase management, querying, stored proceduresPower BIData modeling, DAX, interactive dashboardsExcelPivot table reports, ad-hoc analysisDAX StudioReport optimization and performance tuning
