# 📊 PhonePe Transaction Dashboard - Power BI Project

This Power BI dashboard visualizes and analyzes the digital payment transactions recorded by **PhonePe** across Indian states, districts, and pincodes. The project aims to derive insights into transaction volume, user adoption, regional performance, and temporal patterns using real aggregated data.

---

## 📁 Dataset Overview

The project is built using 8 CSV files:

| File Name             | Description |
|----------------------|-------------|
| `agg_trans.csv`       | Aggregated transaction data by State, Year, Quarter, and Type |
| `agg_user.csv`        | Aggregated user data including Brand and Usage percentage |
| `map_trans.csv`       | District-level transaction data with geo-coordinates |
| `map_user.csv`        | District-level user registration and app opens |
| `top_trans_dist.csv`  | Top districts by transaction amount and count |
| `top_trans_pin.csv`   | Top pincodes by transaction amount and count |
| `top_user_dist.csv`   | Top districts by user count |
| `top_user_pin.csv`    | Top pincodes by registered users |

---

## 🔨 Tools Used

- **Power BI Desktop**
- Power Query Editor (for data transformation and cleaning)
- DAX (Data Analysis Expressions)
- CSV data files from PhonePe Pulse GitHub

---

## ⚙️ Data Cleaning & Transformation

Performed in Power Query Editor:
- Changed column data types (e.g., `Transaction_amount` to Decimal)
- Removed duplicates and null values
- Renamed inconsistent column headers
- Removed unnecessary columns
- Standardized column naming for merging
- Merged and related tables using keys: `State`, `Year`, `Quarter`

---

## 📈 Key DAX Measures

```DAX
Total_Transaction_Amount = SUM('agg_trans'[Transaction_amount])
Total_Transaction_Count = SUM('agg_trans'[Transaction_count])
Transaction_Amount_By_Region = CALCULATE([Total_Transaction_Amount], ALLEXCEPT('agg_trans', 'agg_trans'[Region]))
Transaction_Amount_By_Year_Quarter = CALCULATE([Total_Transaction_Amount], ALLEXCEPT('agg_trans', 'agg_trans'[Year], 'agg_trans'[Quarter]))
Transaction_Amount_By_Type = CALCULATE([Total_Transaction_Amount], ALLEXCEPT('agg_trans', 'agg_trans'[Transaction_type]))
