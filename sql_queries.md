# ✅ SQL QUERIES WITH OUTPUT:

This document enlists all the SQL queries fired on the MS SQL Server to get the values of the corresponding KPI's.
The screenshots of the outputs have also been attached for reference.

## A. KPI’s

### 1. Total Revenue:
```sql
SELECT SUM(total_price) AS total_revenue FROM pizza_sales;
```
Output:
![image](https://github.com/shil5/pizza-sales-project/assets/61142233/4ac77aed-4096-413a-aeb1-3f5c3f312e85)


### 2. Average Order Value (AOV):
```sql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS avg_order_value FROM pizza_sales
```
Output:


### 3. Total Pizzas Sold:
```sql
SELECT SUM(quantity) AS total_pizza_sold FROM pizza_sales
```
Output:


### 4. Total Orders:
```sql
SELECT COUNT(DISTINCT order_id) AS total_orders FROM pizza_sales
 ```
Output:


### 5. Average Pizzas Per Order:
```sql
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS avg_pizzas_per_order
FROM pizza_sales
```
Output:


### B. Daily Trend for Total Orders:
```sql
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
Output:
```
Output:


### C. Monthly Trend for Orders:
```sql
select DATENAME(MONTH, order_date) as month_name, COUNT(DISTINCT order_id) as total_orders
from pizza_sales
GROUP BY DATENAME(MONTH, order_date)
```
Output


### D. % of Sales by Pizza Category
```sql
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
```
Output


### E. % of Sales by Pizza Size
```sql
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size
```
Output
 

### F. Total Pizzas Sold by Pizza Category
```sql
SELECT pizza_category, SUM(quantity) as total_quantity_sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY total_quantity_sold DESC
```
Output

 
### G. Top 5 Pizzas by Revenue
```sql
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
```
Output:

 
### H. Bottom 5 Pizzas by Revenue
```sql
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
 ```
Output:


### I. Top 5 Pizzas by Quantity
```sql
SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
```
Output:

 
### J. Bottom 5 Pizzas by Quantity
```sql
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC
```
Output:


### K. Top 5 Pizzas by Total Orders
```sql
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC
```
Output:

 
### L. Borrom 5 Pizzas by Total Orders
```sql
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC
```
Output:

 
### NOTE
To apply the pizza_category or pizza_size filters to the above queries we need to use WHERE clause. Examples:
```sql
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
WHERE pizza_category = 'Classic'
GROUP BY pizza_name
ORDER BY Total_Orders ASC
```
Output:


