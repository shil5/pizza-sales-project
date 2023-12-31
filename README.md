# 🍕 Pizza Sales Project
(Power BI and SQL Project: creating an interactive dashboard on Pizza Sales and validation using SQL)

### ⏰🏃‍♂️💨 _**Short on time?**_
Directly see this static dashboard pdf: [Pizza Sales Dashboard - NON-interactive PDF](https://github.com/shil5/pizza-sales-project/blob/main/Pizza%20Sales%20Dashboard%20-%20non-interactive.pdf)

**Note:** The above link is not INTERACTIVE, so is not a complete and true showcase of the dashboard. For a full understanding, read this README.

### Contents:
1. [Problem Statement](https://github.com/shil5/pizza-sales-project/blob/main/README.md#problem-statement)
   - A. [KPI's Requirement](https://github.com/shil5/pizza-sales-project/blob/main/README.md#a-kpis-requirement)
   - B. [Charts Requirement](https://github.com/shil5/pizza-sales-project/blob/main/README.md#b-charts-requirement)
2. [Softwares Used (with Versions)](https://github.com/shil5/pizza-sales-project/blob/main/README.md#-softwares-used)
3. [Data Description](https://github.com/shil5/pizza-sales-project/blob/main/README.md#-data-description)
4. [SQL Queries](https://github.com/shil5/pizza-sales-project/blob/main/README.md#-sql-queries)
5. 🌟🌟[Final Dashboard](https://github.com/shil5/pizza-sales-project/tree/main#final-dashboard)

---
<div style="text-align: center;">
   <p><b> Page 1: Home Page ⤵</b></p>
   <img width="748" alt="dashboard page1" src="https://github.com/shil5/pizza-sales-project/assets/61142233/e93ddd88-399f-42cf-9bea-b252f68fec9f">
   <p><b> Page 2: Best/Worst Sellers ⤵</b></p>
   <img width="750" alt="dashboard page2" src="https://github.com/shil5/pizza-sales-project/assets/61142233/c6b346ac-087f-4d8a-aba2-e60bc4d323fd">
</div>


---

## Problem Statement: 

### A. 📏KPI'S REQUIREMENT
We need to analyse key indicators for our pizza sales data to gain insights into our business performance. Specifically, we want to calculate the following metrics:

1. **Total Revenue:** The sum of the total price of all pizza orders.
2. **Average Order Value (AOV):** The average amount spent per order, calculated by dividing the total revenue by the total number of orders.
3. **Total Pizzas Sold:** The sum of the quanitites of all pizzas sold.
4. **Total Orders:** The total number of orders placed.
5. **Average Pizzas Per Order:** The average number of pizzas sold per order, calculated by dividing the total number of pizzas sold by the total number of orders.

### B. CHARTS REQUIREMENT
We would like to visualise various aspects of our pizza sales data to gain insights and understand key trends. We have identified the following requirements for creating charts: 
1. 📊 **Daily Trend for Total Orders:**
Create a bar chart that displays the daily trend of total orders over a specific time period. This chart will help us identify any patterns or fluctuations in order volumes on a daily basis. 
2. 📈 **Monthly Trend for Total Orders:**
Create a line chart that illustrates the hourly trend of total orders throughout the day. This chart will allow us to identify peak hours or periods of high order activity. 
3. 🍩 **Percentage of Sales by Pizza Category:**
Create a pie chart that shows the distribution of sales across different pizza categories. This chart will provide insights into the popularity of various pizza categories and their contribution to overall sales.
4. 🍩 **Percentage of Sales by Pizza Size:**
Generate a pie chart that represents the percentage of sales attributed to different pizza sizes. This chart will help us understand customer preferences for pizza sizes and their impact on sales. 
5. 🌪 **Total Pizzas Sold by Pizza Category:** 
Create a funnel chart that presents the total number of pizzas sold for each pizza category. This chart will allow us to compare the sales performance of different pizza categories. 
6. 📊 **Top 5 Best Sellers by Revenue, Total Quantity and Total Orders:**
Create a bar chart highlighting the top 5 best-selling pizzas based on the Revenue, Total Quantity, Total Orders. This chart will help us identify the most popular pizza options. 
7. 📊 **Bottom 5 Worst Sellers by Revenue, Total Quantity and Total Orders:**
Create a bar chart showcasing the bottom 5 worst-selling pizzas based on the Revenue, Total Quantity, Total Orders. This chart will enable us to identify underperforming or less popular pizza options.

---

## 🛠 SOFTWARES USED
1. **MS Office / Excel:** Version 2019 (v2311)

2. **MS SQL Server:** Version 2022
3. **SQL Server Management Studio (SSMS):** Version 19.2

4. **Power BI:** Version 2.123.742.0 64-bit (November, 2023)

---

## 🔢 Data Description
48621 rows. CSV.
Granularity level: Pizza ID.
1. **pizza_id:** (Primary Key) Unique ID of pizza.
2. **order_id:** Unique ID of order. One order may contain multiple pizzas ordered.
3. **pizza_name_id:** A unique SKU name for Pizza type with description and size, separated by underscores (like, bbq_ckn_l is barbecure chicken pizza of large size)
4. **quantity:** No. of pizzas ordered. Range of values is usually 1 to 7 or 8.
5. **order_date:** Date of order. Format: DD-MM-YYYY
6. **order_time:** Time of order. Format: HH:MM:SS
7. **unit_price:** Price of an individual pizza in dollars. Numerical, float value upto 2 decimal places.
8. **total_price:** Total Price of Pizza in dollars. Numerical, float value upto 2 decimal places. (On first observation, both 7: uni_price = 8: total_price, for all rows. So need to find why 2 duplicate features are needed.)
9. **pizza_size:** Size of Pizza among: S, M and L. (Also present in 3: pizza_name_id)
10. **pizza_category:** Category of Pizza among: Classic, Supreme, Veggie and Chicken.
11. **pizza_ingredients:** Comma-separated List of ingredients of the pizza.
12. **pizza_name:** Name of the Pizza (Consumer-Readable)

---

## ✅ SQL Queries
On SMSS, we run a number of queries to get the outputs which fulfil the KPI requirements. Here is the document with all the queries with screenshotted outputs: [SQL Queries Document](https://github.com/shil5/pizza-sales-project/blob/main/sql_queries.md)

---

## 🚀FINAL DASHBOARD
To take a look at the final Dashboard report:
1. Download the runnable PowerBI file: [Pizza Sales Dashboard - Interactive Runnable](https://github.com/shil5/pizza-sales-project/blob/main/Pizza%20Sales%20Dashboard%20-%20Interactive%20Downloadable.pbix) and open it on your local Power BI Desktop Application, or;
2. Download the PDF file: [Pizza Sales Dashboard - non-interactive PDF](https://github.com/shil5/pizza-sales-project/blob/main/Pizza%20Sales%20Dashboard%20-%20non-interactive.pdf). This will not be interactive and would simply be a collection of all the dashboard pages.

---
THE END


<!--[🔼 Back to top](https://github.com/shil5/pizza-sales-project/blob/main/README.md)-->
