Comprehensive Sales & Customer Analytics Dashboard

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)

Project Overview
An interactive end-to-end Power BI solution designed to analyze $31M in retail sales. The dashboard provides deep insights into financial performance, product profitability, and customer demographics, enabling data-driven decision-making.

Key Features
Sales Intelligence: Tracking Total Sales, Profit, and Average Selling Price across different time periods.
Customer Segmentation: Analysis of 18,400+ customers by age group, occupation, and country (USA, Australia, UK, etc.).
Time Intelligence:  Dynamic YoY Growth and YTD calculations using advanced DAX.
Product Performance:  Identifying top-selling models (Mountain-200 series) and analyzing sales by color and price category.
Python Integration:  Advanced data processing/visualization via Python scripts.

Dashboard Preview
| Sales Overview | Customer Insights |
|---|---|
| ![Sales Tab](Images/Screenshot%202026-02-17%20at%2011.50.46.png?raw=true) | ![Customer Tab](Images/Screenshot%202026-02-17%20at%2011.51.00.png?raw=true) |

| Product Performance | Time Intelligence |
|---|---|
| ![Product Tab](Images/Screenshot%202026-02-17%20at%2011.51.24.png?raw=true) | ![Time Tab](Images/Screenshot%202026-02-17%20at%2011.51.37.png?raw=true) |

Tech Stack & Skills
Data Modeling:  Star Schema (Fact and Dimension tables).
ETL:  Power Query for data cleaning and transformation.
DAX Formulas: `YoY Growth` for year-over-year performance.
`Sales YTD` for cumulative annual sales.
Dynamic segmentation for "Expensive", "Middle", and "Budget" categories.
UI/UX:  Custom navigation buttons, consistent color themes, and drill-through functionality.

Business Insights Derived
1. Bikes is the core revenue driver, accounting for over 80% of total sales.
2. The Adult (30-50) age segment represents the highest-value customer group (56.7%).
3. Black and Red products significantly outperform other colors in the "Bikes" category.
4. Despite high sales, certain "Budget" items have low profit margins, suggesting a need for pricing optimization.

Repository Structure
AdventSalesDataset 1.pbix: The core Power BI project including the data model, DAX measures, and interactive dashboards.
Data/: Contains the raw and processed datasets 
Images/: Screenshots of the dashboard used in this documentation.

