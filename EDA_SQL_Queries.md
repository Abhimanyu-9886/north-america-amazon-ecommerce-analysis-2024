# 📊 SQL Queries Used in EDA

## 1. Top 5 Categories by Total Revenue

**What this query does:**  
This query sums up the total revenue for each unique category in your dataset. It then orders these categories from the highest total_revenue down and gives you the top 5.

**Why we used it:**  
To quickly identify which product categories are the most profitable, helping understand the core business drivers and prioritize efforts.

```sql
SELECT
    category,
    SUM(revenue) AS total_revenue
FROM
    amazon_sales_data
GROUP BY
    category
ORDER BY
    total_revenue DESC
LIMIT 5;
```

---

## 2. Monthly Total Revenue Trend

**What this query does:**  
Groups sales data by month/year (YYYY-MM) and calculates total revenue per month.

**Why we used it:**  
To observe trends and seasonality in sales over time, identify peak performance periods and track growth.

```sql
SELECT
    STRFTIME('%Y-%m', order_date) AS sales_month,
    SUM(revenue) AS monthly_revenue
FROM
    amazon_sales_data
GROUP BY
    sales_month
ORDER BY
    sales_month;
```

---

## 3. Average Return Rate by Country

**What this query does:**  
Calculates the percentage of return_units relative to units_sold for each country.

**Why we used it:**  
To identify countries with high return rates and investigate regional performance issues.

```sql
SELECT
    country,
    SUM(CAST(return_units AS REAL)) AS total_returned_units,
    SUM(units_sold) AS total_units_sold,
    (SUM(CAST(return_units AS REAL)) * 100.0 / SUM(units_sold)) AS average_return_rate_percentage
FROM
    amazon_sales_data
GROUP BY
    country
ORDER BY
    average_return_rate_percentage DESC;
```

---

## 4. Products with Highest Return Units (Top 10)

**What this query does:**  
Aggregates return units by product ID and lists the top 10 most returned products.

**Why we used it:**  
To find products causing the most returns, indicating quality or description issues.

```sql
SELECT
    product_id,
    SUM(return_units) AS total_return_units
FROM
    amazon_sales_data
GROUP BY
    product_id
ORDER BY
    total_return_units DESC
LIMIT 10;
```

---

## 5. Sales Performance by Seller Type and Country

**What this query does:**  
Groups total revenue by seller type and country.

**Why we used it:**  
To assess which seller types perform better across regions and guide fulfillment strategies.

```sql
SELECT
    country,
    seller_type,
    SUM(revenue) AS total_revenue
FROM
    amazon_sales_data
GROUP BY
    country,
    seller_type
ORDER BY
    country,
    total_revenue DESC;
```

---

## 6. Average Rating per Category

**What this query does:**  
Computes average product ratings per category.

**Why we used it:**  
To gauge customer satisfaction by category and identify areas needing improvement.

```sql
SELECT
    category,
    AVG(rating) AS average_rating
FROM
    amazon_sales_data
WHERE
    rating IS NOT NULL
GROUP BY
    category
ORDER BY
    average_rating DESC;
```