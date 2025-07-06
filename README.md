# E-commerce Fulfillment, Inventory & Logistics Optimization Dashboard

This repository presents a supply chain analytics case study using an e-commerce dataset. The project is broken down into five mini-projects to turn transactional data into insights that drive smarter inventory, logistics, and procurement decisions.

**Dataset**: Online Sales Dataset (Kaggle)
**Tools**: SQL (PostgreSQL/MySQL), Python (pandas, seaborn), Power BI
**Topics**: Inventory Optimization, Fulfillment Performance, Procurement Insights, Logistics & Shipping, Demand Pattern Analysis
**Audience**: Supply Chain Teams, Logistics Managers, Inventory Planners, Business Analysts
---
## 📌 Business Context
In this portfolio project, I take on the supply chain analyst role to analyze transactional sales data of a mid-sized e-commerce company. The goal is to provide insights that guide strategic decisions around procurement, inventory stocking, order fulfillment, and shipping performance. 

An real, anonymized e-commerce company - let's refer to it as AmberCom - wants to reduce delays, optimize warehouse operations, and improve product availability. They askes the supply chain analyst to provide data-driven insights to support decisions on:
- What products to reorder
- How to reduce shipping delays and returns
- Which warehouses and shipment providers perform best
- How demand patterns affect procurement and stocking strategy

---

## 🎯 Objectives
Perform data analytics to support inventory and logistics decisions with data-driven insights and dashboard visualizations:

- Analyze product demand trends and seasonality
- Optimize inventory decisions based on velocity and profitability. Identify slow-moving vs. high-velocity SKUs.
- Evaluate fulfillment and shipping performance by warehouse and provider
- Detect fulfillment bottlenecks by region and warehouse
- Reduce returns and delays through root cause insights. Evaluate shipping cost and delivery delays
- Support reorder prioritization based on profitability and risk
- Support procurement prioritization and restocking policies

---
## 🧰 Tools & Technologies

| Tool      | Use Case                                      |
|-----------|-----------------------------------------------|
| **SQL (SQL Server)**   | Query, clean, and transform raw data          |
| **Python (pandas, seaborn, matplotlib)**| KPI calculation, trend analysis, forecasting  |
| **Power BI** | Dashboarding, drill-down reporting        |
| **GitHub**| Project version control and documentation     |

---

## 🗃️ Dataset Overview

| Column              | Description                            |
|---------------------|----------------------------------------|
| InvoiceNo, InvoiceDate | Order ID and date of sale           |
| StockCode, Description | Product ID and name                 |
| Quantity, UnitPrice     | Quantity sold and unit price       |
| CustomerID              | Unique buyer ID                    |
| Country, WarehouseLocation | Customer and fulfillment location |
| Category, SalesChannel  | Product category, online/offline    |
| ReturnStatus           | Indicates if order was returned     |
| Discount, ShippingCost | Pricing and delivery cost info      |
| ShipmentProvider       | Delivery partner                    |
| OrderPriority          | Priority level (High/Medium/Low)    |
| PaymentMethod          | How the customer paid               |

Derived columns:

- `Revenue = Quantity * UnitPrice`

- `Profit = Revenue - Discount - ShippingCost`

- `LeadTime (proxy) = Shipment date - Invoice date`

- `ReturnFlag, ProfitMargin, FulfillmentDelay`
---

## 🧱 Data Pipeline

### 1. 📜 SQL – Data Cleaning & Feature Creation

```sql
-- Extract core fields and compute base revenue
SELECT 
  InvoiceNo,
  InvoiceDate,
  StockCode,
  Quantity,
  UnitPrice,
  Quantity * UnitPrice AS Revenue,
  Discount,
  ShippingCost,
  Country,
  WarehouseLocation
FROM online_sales_data
WHERE ReturnStatus IS NOT NULL;

---

## 🧱 Mini-Project Modules

| Module | Focus Area | Link |
|--------|------------|------|
| 📊 **[Demand Analysis](./demand-analysis/)** | Sales trends, forecasting, seasonality |
| 📦 **[Inventory Analysis](./inventory-performance/)** | Dead stock, velocity, category contribution |
| 🚚 **[Fulfillment & Shipping](./fulfillment-shipping/)** | Delivery delays, shipping cost, providers |
| 🧾 **[Procurement Insights](./procurement-insights/)** | Reorder priority, profit vs return |
| 🔁 **[Return Analysis](./return-analysis/)** | Return rate by product, region, and discount |

---

## 📎 Dataset

- Source: [Online Sales Dataset (Kaggle)](https://www.kaggle.com/datasets/yusufdelikkaya/online-sales-dataset)
- Cleaned dataset included in `/data/online_sales_cleaned.csv`

---

## 🧑‍💻 Author

Nguyen Khanh Linh  
📧 nklinh.620@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/kh%C3%A1nh-linh-nguy%E1%BB%85n-346115176)
