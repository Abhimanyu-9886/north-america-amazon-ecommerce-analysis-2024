# North-america-amazon-ecommerce-analysis-2024
Simulated and analyzed 1M+ Amazon-style e-commerce sales across North America (2024) to uncover trends, customer behavior, return patterns, and seller performance insights.
Project Overview
This project undertakes a comprehensive analysis of a synthetically generated Amazon sales dataset, aiming to extract actionable business insights related to sales performance, revenue trends, product category contributions, return rates, and customer satisfaction. The core objective is to transform raw transactional data into clear, interpretable intelligence, culminating in an interactive Tableau dashboard designed to empower data-driven decision-making.

*Dataset*
The analysis is based on a hypothetical amazon_sales_data.csv dataset. This dataset was programmatically generated using Python (see generate_data.py) to simulate realistic e-commerce transactions for the year 2024. It contains detailed transactional records including:

order_id, order_date

product_id, category, price, rating

units_sold, revenue, return_units

country, seller_type

*Tools & Technologies*

*Data Generation:*

*Python*: Used for programmatically generating the synthetic amazon_sales_data.csv dataset.

*Data Analysis & Manipulation:*

*SQL* (SQLite): For efficient data aggregation and structured querying.

*Python (Pandas)*: For flexible data manipulation, statistical computations, and data preparation.

*Data Visualization & Dashboarding*:

Tableau Public: For creating the interactive and visually compelling dashboard.

*Analysis & Key Findings*
The analysis reveals robust overall performance, with Total Revenue of $178.53M and a Net Revenue of $150.91M, despite 223,118 total units returned. While the USA leads significantly in units sold (823,760), followed by Canada (463,136) and Mexico (363,080), Mexico exhibits the highest return rate, impacting its net revenue. "Electronics" stands out as a top-grossing category. Customer ratings appear uncorrelated with sales volume or price, suggesting other critical satisfaction drivers.

*Dashboard Overview & Interactivity*
The interactive dashboard (available on Tableau Public) provides a comprehensive view of Amazon's e-commerce performance.

*Key Performance Indicators (KPIs)*: Prominently displays Total Revenue, Net Revenue, Total Units Sold, and Total Return Units for an immediate business health overview.

*Detailed Visualizations*: Includes charts for monthly and weekly trends, revenue breakdowns by country, category, and vendor, and country-specific return rates. Product performance is also detailed via average prices and customer ratings by category.

Interactivity: Features interactive filters (e.g., Country, Category) and custom tooltips, allowing users to dynamically explore data and gain granular insights across all visualizations.

🔗 View the Interactive Dashboard on Tableau Public https://public.tableau.com/app/profile/abhimanyu.abhimanyu4716/viz/AmazonSalesAnalysisDashboard_17519219643180/DASH

Business Impact & Recommendations
This project's insights are crucial for strategic decision-making, enabling:

Optimized Sales Strategies: By identifying top-performing categories and understanding revenue trends.

Reduced Return Rates: Pinpointing high-return regions for targeted investigations.

Improved Customer Satisfaction: By understanding factors driving ratings beyond price or volume.

Efficient Resource Allocation: Based on performance across different seller types and geographies.
