# Data Cleaning Log

## Overview
This document outlines the data cleaning and validation process for `raw_orders.xlsx` to produce the analysis-ready `cleaned_orders.xlsx` file.

---

## 1. Cleaning Actions Taken

| Data Issue | Remediation Action |
| :--- | :--- |
| **Duplicates** | Removed 20 duplicate order records based on `order_id`. |
| **Inconsistent Text** | Standardized capitalization in the `ship_mode` column. |
| **Missing Values** | Filled blank entries in Region/State with "Not Specified". |
| **Invalid Discounts** | Replaced negative discount values with `0`. |
| **Calculation Errors** | Recalculated `sales` column to ensure `sales = quantity * unit_price * (1 - discount)`. |

---

## 2. Validation Metrics

* **Total rows in raw data:** 933
* **Total rows in cleaned data:** 913

---

## 3. Conclusion
The dataset has been successfully cleaned, validated, and is ready for KPI reporting and Pivot Table analysis.
