
# 🧪 Exploratory Data Analysis (EDA) Using Pandas

This document presents the Python (Pandas-based) exploratory data analysis performed on the simulated North American e-commerce dataset. It is designed to uncover high-level trends, pricing patterns, customer satisfaction, and return behavior across countries and product categories.

---

## 📌 1. Basic Dataset Health & Structure

```python
import pandas as pd

# Load the dataset
df = pd.read_csv('amazon_sales_data.csv') ## I used google colab so no specific directory, please see Amazon_Synthetic_sales_data_2024.ipynb for generation script.

# Peek at the first few rows
df.head()

# Look at the structure of the data
df.info()

# View summary statistics
df.describe()

# Check for missing values
df.isnull().sum()

# Check tail of the dataset
df.tail()
```

### 🔍 Purpose:
- `head()`, `tail()` give a quick look at the data.
- `info()` helps verify column types and non-null counts.
- `describe()` shows basic stats like mean, std, min, max.
- `isnull().sum()` checks for missing or corrupt values that may affect downstream analysis.

---

## 📌 2. What is the average price of products within each category?

```python
avg_price_by_category = df.groupby('product_category')['sales_amount'].mean().sort_values(ascending=False)
avg_price_by_category
```

### 🔍 Purpose:
To assess how product pricing varies across categories — important for understanding perceived value, premium product segments, and pricing strategy.

---

## 📌 3. What is the market share (by revenue and units) of different seller types?

```python
# Revenue share
revenue_share = df.groupby('seller_type')['sales_amount'].sum().sort_values(ascending=False)

# Unit share
unit_share = df.groupby('seller_type')['order_id'].count().sort_values(ascending=False)
```

### 🔍 Purpose:
To compare the sales contributions of Amazon FBA, 3rd-party vendors, and other seller types. Helps identify which channel dominates in volume and revenue.

---

## 📌 4. What are the monthly and weekly trends for sales and returns?

```python
# Convert order date to datetime
df['order_date'] = pd.to_datetime(df['order_date'])

# Monthly trends
monthly_sales = df.groupby(df['order_date'].dt.to_period('M'))['sales_amount'].sum()
monthly_returns = df[df['is_returned'] == 1].groupby(df['order_date'].dt.to_period('M'))['order_id'].count()

# Weekly trends
weekly_sales = df.groupby(df['order_date'].dt.to_period('W'))['sales_amount'].sum()
weekly_returns = df[df['is_returned'] == 1].groupby(df['order_date'].dt.to_period('W'))['order_id'].count()
```

### 🔍 Purpose:
Reveals seasonal and periodic performance. Peaks in returns or dips in sales may suggest specific challenges or events.

---

## 📌 5. Top-performing product categories by total revenue

```python
top_categories = df.groupby('product_category')['sales_amount'].sum().sort_values(ascending=False).head(10)
top_categories
```

### 🔍 Purpose:
Identifies high-value product segments that drive overall revenue. Useful for targeting promotions or improving supply chain focus.

---

## 📌 6. Average return rate for each country

```python
returns_by_country = df.groupby('country')['is_returned'].mean().sort_values(ascending=False)
returns_by_country
```

### 🔍 Purpose:
Assesses return behavior region-wise, helping understand logistics, customer expectations, or quality issues.

---

## 📌 7. Average customer rating per product category

```python
avg_rating_by_category = df.groupby('product_category')['rating'].mean().sort_values(ascending=False)
avg_rating_by_category
```

### 🔍 Purpose:
Captures customer satisfaction levels for each product group — useful for product development, marketing, and vendor assessments.


