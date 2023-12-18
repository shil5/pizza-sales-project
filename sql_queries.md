⬅ [_Back to project report_](https://github.com/shil5/pizza-sales-project/tree/main)

# ✅ SQL QUERIES WITH OUTPUT:

This document enlists all the SQL queries fired on the MS SQL Server to get the values of the corresponding KPI's.
The screenshots of the outputs have also been attached for reference.

## A. KPI’s

### 1. Total Revenue:
```sql
SELECT
  SUM(total_price) AS total_revenue
FROM pizza_sales;
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/4ac77aed-4096-413a-aeb1-3f5c3f312e85)


### 2. Average Order Value (AOV):
```sql
SELECT
  (SUM(total_price) / COUNT(DISTINCT order_id)) AS avg_order_value
FROM pizza_sales
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/2e8326a1-4a3a-4d8c-9244-8dc146d323a3)


### 3. Total Pizzas Sold:
```sql
SELECT
  SUM(quantity) AS total_pizza_sold
FROM pizza_sales
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/8fe3c06e-843a-48a9-b070-f4216f50366a)


### 4. Total Orders:
```sql
SELECT 
  COUNT(DISTINCT order_id) AS total_orders
FROM pizza_sales
 ```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/7536504f-7d2e-4f3f-836f-26d2fbaeb039)

**Observation:** For an order, we can have >1 pizzas sold. Hence, the following KPI makes sense.

### 5. Average Pizzas Per Order:
```sql
SELECT
  CAST(
       CAST(SUM(quantity) AS DECIMAL(10,2))
       / 
       CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2))
  AS DECIMAL(10,2)
      )
  AS avg_pizzas_per_order
FROM pizza_sales
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/4efff6b8-0349-4e87-9435-91587f8a0f72)

 - - - 

## B. CHARTS

For WHERE filters, see the commented out WHERE clauses. **IMPORTANT:** Here, for the **percentage queries**, when applying WHERE clause in the main query, apply it in the sub_query as well.

### 1. Daily Trend for Total Orders:
```sql
SELECT
  DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
# To apply the month, quarter, week filters to these queries, we need to use WHERE clause as:
# WHERE MONTH(order_date) = 1 # for month filter 
# WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
GROUP BY DATENAME(DW, order_date)
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/44eca127-8cb2-437a-8c00-3d6518b815e2)

### 2. Monthly Trend for Orders:
```sql
SELECT
  DATENAME(MONTH, order_date) AS month_name,
  COUNT(DISTINCT order_id) AS total_orders
FROM pizza_sales
  # WHERE MONTH(order_date) = 1 # for month filter 
  # WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
GROUP BY DATENAME(MONTH, order_date)
ORDER BY total_orders DESC
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/33255ccb-9362-4162-8747-bfe39d9f9757)


### 3. % of Sales by Pizza Category:
```sql
SELECT
  pizza_category,
  CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
  CAST(
        SUM(total_price) * 100
        /
        (
          SELECT SUM(total_price)
          from pizza_sales
          #add WHERE clause if applying outside
          # WHERE MONTH(order_date) = 1 # for month filter 
          # WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
        )
      AS DECIMAL(10,2)) AS percent_sales_category
FROM pizza_sales
# WHERE MONTH(order_date) = 1 # for month filter 
# WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
GROUP BY pizza_category
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/32bcd598-09c9-4141-95c2-20f914dae800)


### 4. % of Sales by Pizza Size:
```sql
SELECT
  pizza_size,
  CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
  CAST(
        SUM(total_price) * 100
        /
        (
          SELECT SUM(total_price)
          from pizza_sales
          #add WHERE clause if applying outside
          # WHERE MONTH(order_date) = 1 # for month filter 
          # WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
        )
      AS DECIMAL(10,2)) AS percent_sales_size
FROM pizza_sales
# WHERE MONTH(order_date) = 1 # for month filter 
# WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
GROUP BY pizza_size
ORDER BY pizza_size
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/d026ceee-1102-4e7d-9ed3-395783cfebb4)

### 5. Total Pizzas Sold by Pizza Category:
```sql
SELECT
  pizza_category,
  SUM(quantity) as total_quantity_sold
FROM pizza_sales
# To apply the pizza_category or pizza_size filters to the above queries we need to use WHERE clause as:
# WHERE pizza_category = 'Classic' # for category filter
# WHERE MONTH(order_date) = 1 # for month filter 
# WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
GROUP BY pizza_category
ORDER BY total_quantity_sold DESC
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/d2c69e61-d427-43f6-85b0-d43b53a0109f)
 
### 6. Top 5 Pizzas by Revenue:
```sql
SELECT
  Top 5 pizza_name,
  SUM(total_price) AS total_revenue
FROM pizza_sales
/* WHERE pizza_category = 'Classic' # for category filter
 WHERE MONTH(order_date) = 1 # for month filter 
 WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
*/
GROUP BY pizza_name
ORDER BY total_revenue DESC
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/33fd6466-fb65-4b62-b0cd-09aa5d68d0c3)

 
### 7. Bottom 5 Pizzas by Revenue:
```sql
SELECT
  Top 5 pizza_name,
  SUM(total_price) AS total_revenue
FROM pizza_sales
/* WHERE pizza_category = 'Classic' # for category filter
 WHERE MONTH(order_date) = 1 # for month filter 
 WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
*/
GROUP BY pizza_name
ORDER BY total_revenue ASC
 ```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/512154d5-dba5-4158-aa0b-59b4c6bb0b92)


### 8. Top 5 Pizzas by Quantity:
```sql
SELECT
  Top 5 pizza_name,
  SUM(quantity) AS total_pizza_sold
FROM pizza_sales
/* WHERE pizza_category = 'Classic' # for category filter
 WHERE MONTH(order_date) = 1 # for month filter 
 WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
*/
GROUP BY pizza_name
ORDER BY total_pizza_sold DESC
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/25f630aa-fdc7-4daf-a298-c233b535e6b1)

 
### 9. Bottom 5 Pizzas by Quantity:
```sql
SELECT
  TOP 5 pizza_name,
  SUM(quantity) AS total_pizza_sold
FROM pizza_sales
/* WHERE pizza_category = 'Classic' # for category filter
 WHERE MONTH(order_date) = 1 # for month filter 
 WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
*/
GROUP BY pizza_name
ORDER BY total_pizza_sold ASC
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/76fd4f86-a5f9-40df-97ee-2be17ca89a34)


### 10. Top 5 Pizzas by Total Orders:
```sql
SELECT
  Top 5 pizza_name,
  COUNT(DISTINCT order_id) AS total_orders
FROM pizza_sales
/* WHERE pizza_category = 'Classic' # for category filter
 WHERE MONTH(order_date) = 1 # for month filter 
 WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
*/
GROUP BY pizza_name
ORDER BY total_orders DESC
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/6ffebddf-c9c1-4871-ad85-8435a768108c)

 
### 11. Bottom 5 Pizzas by Total Orders:
```sql
SELECT
  Top 5 pizza_name,
  COUNT(DISTINCT order_id) AS total_orders
FROM pizza_sales
/* WHERE pizza_category = 'Classic' # for category filter
 WHERE MONTH(order_date) = 1 # for month filter 
 WHERE DATEPART(QUARTER, order_date) = 1 # for quarter filter
*/
GROUP BY pizza_name
ORDER BY total_orders ASC
```
Output:

![image](https://github.com/shil5/pizza-sales-project/assets/61142233/02100fa8-46d6-4b48-bea9-0dbb8f0b7f30)

⬅ [_Back to project report_](https://github.com/shil5/pizza-sales-project/tree/main)
