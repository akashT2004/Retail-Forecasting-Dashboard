# SuperStore Forecasting Dashboard Rebuild

This project is of the SuperStore retail forecasting and performance dashboard. It starts with raw SuperStore transaction data, cleans and transforms it in a Jupyter notebook, and then uses the exported CSV files inside Power BI to build a multi-page dashboard.

## Project Goal

The main goal of this project is to turn raw retail data into a business dashboard that helps answer these questions:

- How is sales performance trending?
- Which products, regions, and categories perform best?
- Which products are likely to run out of stock soon?
- Which products and cities have high return rates?
- Which products are profitable and which are loss-making?

The final output is a Power BI dashboard with four main pages:

- Page 1: Executive sales overview
- Page 2: Inventory and stockout analysis
- Page 3: Return analysis
- Page 4: Profitability analysis

---

## Folder Structure

```text
SuperStore-Forecasting-Rebuild/
├── 01_eda_cleaning.ipynb
├── data/
├── notebook/
├── outputs/
├── Power BI Dashboard.pbix
├── SuperStore_Dashboard_Explanation.docx
└── README.md
```

## Data Sources

The project uses the following input files from the `data/` folder:

- `SuperStore_Sales_Enhanced.csv`
- `customer_maste.csv`
- `product_master.csv`
- `returns.csv`

These files contain the raw retail transaction data, customer details, product master information, and returns information.

---

## Notebook: `01_eda_cleaning.ipynb`

The notebook is the data preparation stage of the project. It is used to clean the original data and create analysis-ready output files for Power BI.

### What the notebook does

- Loads the raw SuperStore sales dataset
- Checks missing values and data types
- Renames confusing columns into simpler names
- Converts order date and ship date into proper date formats
- Removes unnecessary columns that are not needed in the final dashboard
- Converts Sales, Quantity, and Profit into numeric fields
- Saves cleaned and transformed outputs into the `outputs/` folder

### Why this step is important

Power BI works best when the data is already cleaned and structured. The notebook makes the dataset ready for visualization by removing noise, fixing types, and creating separate output tables for different dashboard pages.

---

## Output Files

The notebook creates several analysis files in the `outputs/` folder.

### Main cleaned sales file

- `clean_sales_data.csv`

This is the main file used for Page 1, the executive dashboard.

### Inventory files

- `model1_inventory_summary.csv`
- `model1_stockout_alerts.csv`

These files support the inventory / stockout page.

### Return analysis files

- `model2_product_return_rates.csv`
- `model2_city_return_rates.csv`
- `model2_category_return_trend.csv`

These files support the return analysis page.

### Profitability files

- `model3_product_profitability.csv`
- `model3_best_sellers.csv`
- `model3_loss_makers.csv`
- `model3_high_rev_low_margin.csv`

These files support the profitability page.

### Forecast images

- `forecast_west_technology.png`
- `prophet_overall_forecast.png`
- `prophet_components.png`
- `prophet_components_west_tech.png`
- `sales_by_category.png`
- `sales_by_region.png`
- `monthly_sales_trend.png`

These are used for forecasting and trend display.

---

## Power BI Dashboard Pages

## Page 1 - Sales Overview

This is the main executive dashboard page. It gives a quick summary of business performance.

### Visuals used

- KPI cards for `Sum of Sales`, `Sum of Profit`, and `Sum of Quantity`
- Region slicer buttons
- Donut chart for `Sales by Segment`
- Line chart for `Sales by Month and Year`
- Bar chart for `Sales by Warehouse`
- Map for `Profit by State`
- Donut chart for `Sales by Region`
- Line chart for `Profit by Month and Year`
- Bar chart for `Sales by Category`
- Bar chart for `Sales by Sub-Category`

### Purpose

The purpose of this page is to give a top-level summary of the business in one screen. It shows how much was sold, how much profit was made, which regions perform well, and how sales are distributed across segments and product groups.

---

## Page 2 - Inventory / Stockout Analysis

This page is used to find products that are close to running out of stock.

### Visuals used

- Table visual with inventory data
- Conditional formatting on `days_to_stock_out`

### Fields used

- `Product ID`
- `Product Name`
- `Warehouse`
- `Current_Stock`
- `Reorder_Level`
- `stock_remaining`
- `days_to_stock_out`

### Highlighting used

- Rows where `days_to_stock_out` is low were highlighted in red
- The alert file was used to support the warning logic

### Purpose

The purpose of this page is to help identify products that may go out of stock soon, so replenishment decisions can be made early.

---

## Page 3 - Returns Analysis

This page is used to analyze product and city return behavior.

### Visuals used

- Product return rate table
- City return rate table

### Fields used in the top table

- `Product ID`
- `Product Name`
- `Category`
- `Segment`
- `total_orders`
- `total_returns`
- `return_rate`

### Fields used in the bottom table

- `City`
- `total_orders`
- `total_returns`
- `return_rate`

### Highlighting used

- `return_rate >= 0.20` was highlighted in red

### Purpose

The purpose of this page is to identify products and cities with high return behavior. This helps investigate possible quality, delivery, or customer experience issues.

---

## Page 4 - Profitability Analysis

This page is used to evaluate product-level profitability.

### Visuals used

- Profitability table
- Conditional formatting on `total_profit` and `profit_margin`

### Fields used

- `Product ID`
- `Product Name`
- `total_sales`
- `total_quantity`
- `total_profit`
- `profit_margin`

### Highlighting used

- Negative `total_profit` values were highlighted in red
- Negative `profit_margin` values were highlighted in red

### Purpose

The purpose of this page is to identify profitable products, weak-margin products, and loss-making products. It helps the user understand which products create value and which products may need attention.

---

## Overall Dashboard Story

The dashboard follows a complete workflow:

1. Raw SuperStore data is cleaned in Python.
2. The cleaned data is exported into multiple CSV files.
3. Power BI imports those files.
4. Each page focuses on a different business question.
5. Conditional formatting is used to make risky items easy to spot.

### Business value

This dashboard helps answer four main business areas:

- Sales performance
- Inventory risk
- Return analysis
- Profitability analysis

The goal is to make decision-making faster and easier by converting raw data into a visual summary.

---

## How to Use the Project

1. Open `01_eda_cleaning.ipynb` if you want to review the cleaning and output generation steps.
2. Open `Power BI Dashboard.pbix` in Power BI Desktop.
3. Use the imported CSV files from the `outputs/` folder.
4. Navigate through Page 1 to Page 4 to see the complete analysis.

---

## Summary

This rebuild project demonstrates how raw retail data can be turned into a professional dashboard using Python and Power BI. The notebook prepares the data, the output files store the analysis tables, and the dashboard presents the final story clearly for business users.
