# E-commerce Fulfillment, Inventory & Logistics Optimization Dashboard

This repository presents a supply chain analytics case study using an e-commerce dataset. The project is broken down into five mini-projects to turn transactional data into insights that drive smarter inventory, logistics, and procurement decisions.

**Dataset**: Online Sales Dataset (Kaggle)

**Tools**: SQL (PostgreSQL/MySQL), Python (pandas, seaborn), Power BI

**Topics**: Inventory Optimization, Fulfillment Performance, Procurement Insights, Logistics & Shipping, Demand Pattern Analysis

**Audience**: Supply Chain Teams, Logistics Managers, Inventory Planners, Business Analysts

---

## 📌 Business Context
In this portfolio project, I take on the supply chain analyst role to analyze transactional sales data of a mid-sized e-commerce company. The goal is to provide insights that guide strategic decisions around procurement, inventory stocking, order fulfillment, and shipping performance. 

An e-commerce company called AmberCom wants to reduce delays, optimize warehouse operations, and improve product availability. They askes the supply chain analyst to provide data-driven insights to support decisions on:
- What products to reorder
- How to reduce shipping delays and returns
- Which warehouses and shipment providers perform best
- How demand patterns affect procurement and stocking strategy

---

## 🎯 Objectives
Perform data analytics to support inventory and logistics decisions with data-driven insights and dashboard visualizations:

- Analyze product demand trends and seasonality
- Optimize inventory decisions by identify slow-moving vs. high-velocity SKUs
- Evaluate fulfillment and shipping performance by warehouse and provider
- Evaluate shipping cost and delivery delays
- Support procurement prioritization and restocking policies profitability and risk

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

The dataset comprises anonymized data on online sales transactions, capturing various aspects of product purchases, customer details, and order characteristics.
- Source: [Online Sales Dataset (Kaggle)](https://www.kaggle.com/datasets/yusufdelikkaya/online-sales-dataset)
- Cleaned dataset included in `/data/online_sales_cleaned.csv`


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
```

- Normalize `Category, ReturnStatus, ShipmentProvider`

- Extract `YEAR, MONTH, WEEKDAY from InvoiceDate`

- Handle missing `CustomerID, WarehouseLocation, ShipmentProvider`

### 2. 🐍 Python – EDA & KPI Engineering

- Load SQL export into pandas
- Calculate:

  - Profit = Revenue - Discount - ShippingCost

  - ProfitMargin, AvgLeadTime, ReturnRate

- Use seaborn/matplotlib to explore:

  - Category trends

  - Fulfillment delays

  - Return patterns

---

### 3. 📊 Power BI – Interactive Dashboard
Connect cleaned .csv to Power BI

Build data model with Date, Product, Region dimensions

Create visual modules:

KPI Cards (Profit, Revenue, Delay)

Category performance tree map

Region vs. Shipping Provider heatmap

Return Rate by Warehouse bar chart

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

## 🔍 Analysis Sections
### 📈 A. Demand Pattern & Forecasting
Monthly sales trends by category and region

Seasonality detection (by quarter/month)

Forecast using rolling averages or Prophet

### 📦 B. Inventory Optimization
Identify dead stock SKUs

ABC classification of products

Inventory prioritization by demand velocity and margin

### 🚚 C. Fulfillment & Shipping Analysis
Avg delay by ShipmentProvider and WarehouseLocation

Shipping cost as % of order value

Delivery issues linked to return rate

### 🧾 D. Procurement & Reorder Insights
Reorder priority based on margin and demand variability

Detect over-discounted products with low returns

Category risk score: demand × return rate

### 🔁 E. Return Behavior Analysis
Correlation: Discount vs Return Rate

Return patterns by SalesChannel and PaymentMethod

Region/product-specific return hotspots

---

## 📌 Key KPIs

| **Metric**         | **Description**                             |
|--------------------|---------------------------------------------|
| `AvgLeadTime`      | Average shipping delay in days              |
| `ReturnRate`       | % of orders returned                        |
| `ShippingCost %`   | ShippingCost / Revenue                      |
| `SKU Velocity`     | Orders per SKU per month                    |
| `ProfitMargin`     | Profit as a % of revenue                    |
| `DeadStockFlag`    | SKU with no orders in X days                |

---

## 📎 Deliverables
- ✅ .sql scripts (data cleaning + transformations)

- ✅ Python notebooks (EDA, KPI calculations, forecasting)

- ✅ Power BI dashboard (.pbix)

- ✅ PDF report: key insights + business recommendations

- ✅ Full GitHub repository with documentation, visuals, and code

---

## 🧠 Sample Insights (Business Value)
- 21% of SKUs contribute less than 1% of profit → flag for review

- Shipping Provider C has 2x average delay → performance contract review

- Discounts >20% lead to 35% higher return rates in Category A

- Warehouse B has highest cost-to-serve per unit shipped → consider rebalancing stock

---

## 🚀 Future Improvements
- Integrate real shipment tracking to improve lead time accuracy

- Build a simulation on “what if” warehouse consolidation

- Add inventory holding cost calculation to procurement model

- Create automated alert system for return spikes or shipping delays


## 🧑‍💻 Author

Nguyen Khanh Linh  
📧 nklinh.620@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/kh%C3%A1nh-linh-nguy%E1%BB%85n-346115176)
