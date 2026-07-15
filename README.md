# Product Sales Enterprises Analysis
An end-to-end data analytics project focused on cleaning, transforming, and modeling raw product sales and inventory data using Excel and Power Query, followed by building interactive business intelligence dashboards in Power BI.

## 📌 Project Overview & Objective
The objective of this project is to implement data pre-processing and data modeling techniques to convert messy, raw retail and online data into actionable business insights. The project covers the full spectrum of data analytics—Descriptive, Diagnostic, Predictive, and Prescriptive—to evaluate revenue performance, regional operations, marketing channels, and warehouse health.

## 🛠️ Tools & Technologies Used

•	**Excel & Power Query**: Data cleaning & Transformaing

•	**Power BI**: Data modeling (Star Schema), DAX calculations, and interactive multi-dashboard visualization.

## 📂 Project Architecture & Data Workflow
## 1. Data Pre-Processing (Excel & Power Query)

•	**Data Cleaning:** Removed duplicates and handled missing values.

•	**Formatting:** Standardized data types (e.g., forcing raw text into clean Date/Time structure).

•	**Feature Engineering:**  Created custom columns using Excel formulas.

    o	Stock Status: =IF([@QuantityInStock]<=[@ReorderPoint],"⚠ Reorder Now ", "✅ Stock OK")
    
    o	Sales Channel: =IF(LEFT([@OrderID],1) = "O", "Online", "Retail")


## 2. Data Modeling (Power BI)

The data was decoupled into a highly efficient Star Schema (Many-to-One & One-to-One Relationships) linking a central transactional table to distinct dimensions:

•	Fact_Sales ─── Dim_Product_Details (M:1)

•	Fact_Sales ─── Dim_Location (M:1)

•	Fact_Sales ─── Dim_Time_Details (M:1) 

•	Fact_Sales ─── Dim_Sales_Order_Details (1:1) 

•	Fact_Sales ─── Inventory_Tracking (M:1) 

## 4. DAX Measures Implemented

    •	Store Performance: Rev Per Store = DIVIDE ([Regional Revenue], DISTINCTCOUNT (Dim_Location [StoreID]), 0) 

    •	Inventory Value: Total Stock Value = SUM (Inventory_Tracking [Stock Value])

    •	Transaction Count: Order count = DISTINCTCOUNT (Fact_Sales [OrderID]) 

    •	Supply Chain Alert: Low Stock Count = CALCULATE(COUNTROWS(Inventory_Tracking))

## 📊 Dashboard Visualizations
## Dashboard 1: Sales & Operational Performance

•	KPI Cards ─── Total Revenue, Online Revenue, Retail Revenue 

•	Donut Chart ─── Revenue breakdown by product category 

•	Cluster Bar Charts ─── Performance ranking by Store Location and Regional Manager 

•	Cluster Column Charts ─── Referral source performance and review/feedback analysis 

## Dashboard 2: Inventory Health & Predictive Forecasting

•	KPI Cards ─── Total Stock Value, Total Stock Quantity 

•	Donut Chart ─── Low stock count grouped by Supplier.

•	Tree Map ─── Storage location capacity grouped by Stock Status.

•	Matrix Tables ─── Purchase prediction matrices based on marketing referral and time-of-day trend.

## 📈 Key Insights & Findings

 •	  **Revenue Stream:** Total revenue reached $3.47M across ~3,200 orders, heavily driven by Retail Sales ($2.27M) compared to Online Sales ($1.26M).

 •	  **Product Dominance:** Electronics led sales significantly at $19.7M, followed by Furniture ($9.7M) and Office Supplies ($5.2M).

 •	  **Top Performers:** Store B brought in the highest revenue ($0.88M), with Eric emerging as the top-performing Regional Manager ($1.36M in the East region).

 •	  **Consumer Behavior:** Mondays and Tuesdays are peak brick-and-mortar retail days. Online shoppers highly prefer using Debit Cards over Gift Cards.

•	**Logistics & Risk:** Total stock sits healthy at $12.84M across 126K units. Low-stock vulnerabilities are perfectly distributed across 4 main suppliers, minimizing single-source dependency risks.

## 🏁 Conclusion

This integration successfully highlights how utilizing Excel for localized data pre-processing coupled with the relational modeling power of Power BI yields an efficient, enterprise-ready BI reporting pipeline.






