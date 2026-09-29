# 📊 Retail Sales Analysis Dashboard

## 🛠️ Project Overview
This interactive Power BI dashboard provides a deep-dive analysis of retail sales performance. By consolidating data across products, regions, and delivery streams, the report delivers actionable insights into revenue drivers, fulfillment efficiency, and customer purchasing behavior to help stakeholders optimize supply chain and marketing strategies.

---

## 🎬 Live Dashboard Preview

<img width="1435" height="798" alt="Screenshot 2026-09-27 122601" src="https://github.com/user-attachments/assets/63192bc6-094a-49e5-8003-95dba29f0f04" />

---

## 📥 Access the Source Files
* 📁 **[Download the Power BI File (.pbix)](./RetailPulse_PowerBI.pbix)**


---

## 📈 Key Business Metrics Tracked (Snapshot)
* **Total Revenue:** \$261.60K
* **Total Orders:** 3,000 (3K)
* **Total Quantity Sold:** 9,000 (9K)
* **Total Unique Customers:** 498

---

## 💡 Key Business Insights from the Visuals

### 1. Delivery & Fulfillment  (`Total Revenue by Delivery_status`)
* **Insight:** Out of the \$261.60K total revenue, **Delivered** orders make up the largest share (\$106.32K), closely followed by **Delayed** orders (\$95.50K). 
* **Actionable Strategy:** Delayed orders represent a massive portion of total business volume, indicating a critical bottleneck in the logistics or shipping pipeline that requires immediate operational review.

### 2. Transaction Methods (`Total Revenue by Payment_method`)
* **Insight:** **Credit Cards** drive the highest revenue block (\$125.41K), representing nearly half of all sales. Credit card transactions outperform Bank Transfers, PayPal, and Cash on Delivery (CoD) options combined.

### 3. Product Performance & Mix
* **Top Categories:** **Cleaning** products lead revenue generation, followed closely by Kitchen, Outdooors, Personal Care, and Storage categories.
* **Top Individual Item:** **Kitchen Product 53** stands out as the single highest revenue-generating SKU in the entire product inventory.

---

## ⚙️ Technical Architecture

### 1. Data Cleaning & Transformation (Power Query)
* **Text Formatting:** Standardized irregular product names and categorized raw entries into clean product buckets (*Cleaning, Kitchen, Outdoors, Personal Care, Storage*).
* **Delivery Profiling:** Conditional columns were mapped out to separate and track explicit delivery states (*Delivered, Delayed, Cancelled*).

### 2. Data Modeling (Star Schema)
The architecture uses a central sales transaction table connected cleanly to multiple dimension layers:
* **Fact Table:** `Fact_Sales` (Stores quantities, costs, dates, and keys)
* **Dimension Tables:** `Dim_Products` (SKUs, Names, Categories), `Dim_Customers`, and `Dim_Geography` (Regions: *Central, East, North, South, West*).

### 3. DAX Calculations
Here are examples of core metrics formulated within the report to run these visual matrices:

```dax
// 1. Core Revenue Aggregation
Total Revenue = SUM(Fact_Sales[Revenue_Amount])

// 2. Customer Acquisition Tracking
Total Customers = DISTINCTCOUNT(Fact_Sales[Customer_ID])

// 3. Conditional Revenue Breakdown Example
Delivered Revenue Only = 
CALCULATE(
    [Total Revenue], 
    Dim_Fulfillment[Delivery_status] = "Delivered"
)
```

---

## 🎨 Visual Design & UI Features
* **Color Identity:** Dark-mode dashboard built using deep blue container frames and bright cyan accents for ideal visual contrast.
* **Slicer Panels:** Interactive top and right filters let users slice data cleanly by **Delivery Status**, **Product Categories**, and **Geographic Regions** (*Central, East, North, South, West*).
