# 📊 Power BI Sales Dashboard

This project presents a **comprehensive sales analytics dashboard** created in **Power BI**, designed to visualize key business performance indicators (KPIs) such as sales, profit, orders, and profit margin.  
It provides actionable insights into year-over-year growth, top-performing products, cities, and sales channels through interactive visualizations and dynamic filters.

---

## 🚀 Dashboard Overview

### 🎯 **Project Objectives**
This project demonstrates how to:
- Calculate and visualize **total sales**, **profit**, **orders**, and **profit margin**.
- Compare **year-over-year (YoY)** performance by product, month, and sales channel.
- Analyze **customer sales** and identify **top-performing locations**.
- Build **interactive dashboards** using slicers for user-friendly filtering by Date, City, Product, and Channel.

---

## 🌟 **Key Features**

| Feature | Description |
|----------|-------------|
| 📈 **Total Sales Overview** | Displays complete sales metrics for any selected period. |
| 💰 **Profit & Margin Analysis** | Highlights profitability across products, customers, and regions. |
| 🔄 **Year-over-Year Comparison** | Compares sales and profit growth trends with the previous year. |
| 🏙️ **Top 5 Cities Analysis** | Identifies top-performing cities to focus marketing strategies. |
| 👥 **Customer Insights** | Provides a detailed look at sales by customer and product segment. |
| 🎛️ **Dynamic Slicers** | Enables filtering by **Date**, **City**, **Product**, and **Channel**. |

---

## 🧠 **Skills Demonstrated**

- Power BI **Data Visualization & Dashboard Design**
- **Data Cleaning** and transformation using Power Query
- **Data Modeling** and relationship creation
- **DAX (Data Analysis Expressions)** calculations
- **Business Intelligence (BI)** storytelling and performance analysis

---

## 🧩 **Step-by-Step Process**

### 1️⃣ **Data Collection**
Sample sales dataset (`Sales.csv`) containing transaction-level details (Order ID, Product, Category, Region, Sales, Profit, etc.) was used as the base.

### 2️⃣ **Data Preparation (Power Query)**
Performed essential **ETL (Extract, Transform, Load)** tasks:
- Removed duplicates and handled missing values.
- Merged tables and standardized column names.
- Created calculated columns for cleaner analysis.

### 3️⃣ **Create a Date Table (DAX)**
To enable time-intelligent calculations:
```DAX
DateTable =
ADDCOLUMNS (
    CALENDARAUTO(),
    "Year", YEAR([Date]),
    "Quarter", "Q" & FORMAT(CEILING(MONTH([Date])/3, 1), "#"),
    "Quarter No", CEILING(MONTH([Date])/3, 1),
    "Month No", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMMM"),
    "Month Short Name", FORMAT([Date], "MMM"),
    "Month Short Name Plus Year", FORMAT([Date], "MMM,yy"),
    "DateSort", FORMAT([Date], "yyyyMMdd"),
    "Day Name", FORMAT([Date], "dddd"),
    "Details", FORMAT([Date], "dd-MMM-yyyy"),
    "Day Number", DAY([Date])
)
````

---

### 4️⃣ **Data Modeling**

* Established relationships between the **Sales** and **DateTable** tables.
* Defined keys and hierarchies for consistent aggregation.
* Created a star schema model for efficiency.

---

### 5️⃣ **Develop Power BI Reports**

Created multiple visuals and interactive reports including:

* **Sales by Product (YoY comparison)**
* **Sales by Month (YoY comparison)**
* **Top 5 Cities by Sales**
* **Profit by Channel**
* **Sales by Customer**
* KPI cards for **Sales**, **Profit**, **Profit Margin**, and **Products Sold**

---

## 🧮 **Key DAX Calculations**

```DAX
Sales = SUM(Sales_Data[Sales])

Sales PY = CALCULATE([Sales], SAMEPERIODLASTYEAR(DateTable[Date]))
Sales vs PY = [Sales] - [Sales PY]
Sales vs PY % = DIVIDE([Sales vs PY], [Sales], 0)

Profit = SUM(Sales_Data[Profit])
Profit LY = CALCULATE([Profit], SAMEPERIODLASTYEAR(DateTable[Date]))
Profit vs LY = [Profit] - [Profit LY]
Profit vs LY % = [Profit vs LY] / [Profit]

Profit Margin = DIVIDE([Profit], [Sales], 0)
```

---

## 🧭 **Dashboard Insights**

* 📉 Sales decreased by **10% in 2019** compared to the previous year.
* 🛍️ **Top 7 products** saw a decline in overall sales.
* 👥 Four key customers contributed to the majority of sales drop.
* 🌍 **Export channel** maintained a higher profit margin than domestic.

---

## 💡 **Business Impact**

This dashboard empowers management to:

* Monitor KPIs in real-time.
* Identify underperforming areas.
* Plan sales strategies and marketing focus.
* Evaluate yearly performance improvements.

---

## 🛠️ **Tools & Technologies**

| Tool                | Purpose                                   |
| ------------------- | ----------------------------------------- |
| 🟨 Power BI Desktop | Data visualization and dashboard building |
| 🧮 DAX              | Calculations and measures                 |
| 🧰 Power Query      | Data cleaning and transformation          |
| 📊 Excel / CSV      | Source data format                        |


## 🏁 **Conclusion**

This project demonstrates the end-to-end process of **data cleaning, modeling, DAX calculation, and visualization** using Power BI.
The resulting dashboard enables insightful business decisions through interactive and meaningful visual analytics.

---

### ⭐ *If you found this project useful, please give it a star on GitHub!*

```

---

Would you like me to make this README **with a screenshot layout section (boxes showing where to add images)** — so you can visually match your dashboard sections later?  
It’ll look even more professional when you upload it to GitHub.
```
