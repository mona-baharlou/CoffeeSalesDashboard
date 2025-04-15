# Kraken Koffee Sales Dashboard (PowerBI)

![Dashboard Preview](https://github.com/mona-baharlou/CoffeeSalesDashboard/blob/main/sales_page-0001.jpg)

A dynamic PowerBI dashboard analyzing sales performance, product trends, store metrics, and forecasts for Kraken Koffee. Built using **CSV data**, **Power Query**, and **DAX measures** to deliver actionable insights.

## 📊 Features

### 1. **Sales Overview**
   - **Key Metrics**: Total transactions (`149,116`), total sales (`$698,812`), average order size (`$4.69`), stores (`3`), products (`80`).
   - **Top Performers**: "Davy Jones' Sustainably Crown" (Top Earner), "Crow's Nest Croissant" (Most Popular Product).

   ![](https://github.com/mona-baharlou/CoffeeSalesDashboard/blob/main/kraken1.png)

### 2. **Product Performance**
   - **Category Breakdown**: Coffee (`$14,447K`), Tea (`$1,444K`), Bakery (`$8,225K`), with DAX-driven percentage contributions.
   - **Top 10 Products**: Ranked using DAX measures (e.g., `RANKX()`).
   - **Store-Level Insights**: Average order size by location (e.g., Tampa: `$4.51`) calculated with Power Query and DAX.

   ![](https://github.com/mona-baharlou/CoffeeSalesDashboard/blob/main/kraken2.png)

### 3. **Store Analytics**
   - **Daily & Monthly Sales**: Aggregated by Power Query for Miami, Orlando, and Tampa (Jan-Jun totals).
   - **2023 Forecast**: DAX-based forecast measures (`$468,337`).

![](https://github.com/mona-baharlou/CoffeeSalesDashboard/blob/main/kraken3.png)

### 4. **Forecasts & Trends**
   - **Monthly Forecasts**: Time-intelligence DAX functions for projections.
   
![](https://github.com/mona-baharlou/CoffeeSalesDashboard/blob/main/kraken5.png)

### 5. **Data Pipeline**
   - **Power Query**: Cleaned and transformed raw CSV data (e.g., date formatting, merging tables).
  - **Cumulative Forecast Logic**: DAX-driven rolling forecast using time intelligence:
     ```dax
     Forecast = 
     CALCULATE(
         SUMX(
             VALUES('Forecast Date Table'[Date]),
             [AVG Daily Sales By Total Sales]
         ),
         FILTER(
             ALLSELECTED('Forecast Date Table'[Date]),
             'Forecast Date Table'[Date] <= MAX('Forecast Date Table'[Date])
         )
     )
     ```

## 🛠️ Technical Implementation
- **Data Source**: CSV files for transactions, products, and store details.
- **Power Query**: Used for:
  - Data cleaning (e.g., handling nulls, type conversion).
  - Merging tables (e.g., linking products to sales).
  - Creating calculated columns (e.g., `Month Name`, `Day of Week`).
- **DAX**: Measures for:
  - Aggregations (`SUMX`, `AVERAGE`).
  - Rankings (`TOPN`, `RANKX`).
