# Olist Sales & Revenue Analytics Dashboard (Power BI)

A 4-page Power BI dashboard built on the **Olist Brazilian E-Commerce** dataset to analyze marketplace performance across **sales**, **delivery SLA**, **customer insights**, and **payment behavior**.  
This project demonstrates an end-to-end BI workflow: **Power Query cleaning**, **star-schema style modeling**, and **DAX measures** for KPI reporting.

## Dashboard Pages
1. **Executive Overview**
   - Core KPIs (Sales, Orders, AOV, Review Score, Late Delivery Rate)
   - Sales trend over time
   - Sales breakdown by category and state

2. **Sales Deep Dive**
   - Category → product drilldown (matrix)
   - Top products and top sellers (Top N)
   - Product/category contribution analysis

3. **Delivery & SLA**
   - Average delivery days and late delivery rate
   - Late delivery trends over time
   - Root-cause views by state/category/seller
   - Delivery impact on review scores (scatter)

4. **Customer Insights**
   - Unique customers and customer trend over time
   - Customer geography (top states/cities)
   - Orders and sales distribution by location

## Key KPIs (DAX Measures)
- **Sales (Items)** = Sum of item price from `OrderItems`
- **Orders** = Distinct count of `order_id`
- **AOV** = Sales / Orders
- **Avg Review Score** = Average of `review_score` (when available)
- **Avg Delivery Days** = Average delivery duration (delivered orders)
- **Late Delivery Rate** = % delivered orders delivered after estimated date
- **Paid Amount** = Sum of `payment_value` from `Payments`
- **MoM / YoY Growth** (time intelligence using `DimDate`)

## Data Model (Star Schema Style)
- **Orders** acts as the order header/bridge table
- **OrderItems** is the main fact table (sales at item level)
- **Payments** and **Reviews** connect to Orders by `order_id`
- Dimensions: **Products**, **Customers**, **Sellers**, and **DimDate**

Main relationships:
- `Orders[order_id]` → `OrderItems[order_id]`
- `Orders[order_id]` → `Payments[order_id]`
- `Orders[order_id]` → `Reviews[order_id]`
- `Products[product_id]` → `OrderItems[product_id]`
- `Sellers[seller_id]` → `OrderItems[seller_id]`
- `Customers[customer_id]` → `Orders[customer_id]`
- `DimDate[Date]` → `Orders[Order Date]`

## Dataset
This project uses the **Brazilian E-Commerce Public Dataset by Olist** from Kaggle.


## Files in This Repository
- `powerbi/olist-powerbi-dashboard.pbix` — Power BI dashboard file
- `screenshots/` — dashboard and model screenshots (optional but recommended)
- `README.md` — project documentation

## How to Open
1. Download the `.pbix` file from `powerbi/`
2. Open it using **Power BI Desktop**
3. If needed, update data source paths:
   - **Transform data → Data source settings**
4. Refresh the model:
   - **Home → Refresh**

## Screenshots 
Add your screenshots here once uploaded:
- `screenshots/page1_overview.png`
- `screenshots/page2_sales.png`
- `screenshots/page3_delivery.png`
- `screenshots/page4_customers.png`
- `screenshots/model_view.png`

## Tools Used
- Power BI Desktop (Power Query + DAX)
- GitHub (version control + project sharing)

## Author
 **Nader Othman**

