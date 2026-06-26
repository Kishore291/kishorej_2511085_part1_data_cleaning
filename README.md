# Part 1: Business Data Cleaning, Validation & Excel Reporting

## 1. Problem Summary
This repository contains the completion of Part 1 of the Business Analytics Capstone Project. The objective of this phase is to take raw, messy order-level sales data from multiple internal systems, clean it, validate it against strict business rules, and produce analysis-ready financial reports.

## 2. Dataset Description
* **File Name:** `raw_orders.xlsx` (Cleaned output: `cleaned_orders.xlsx`)
* **Initial Size:** 933 rows
* **Cleaned Size:** 913 rows
* **Contents:** Transactional sales data including order IDs, shipping modes, geographical data, product pricing, and applied discounts.

## 3. Tools Used
* **Microsoft Excel:** Data Cleaning, Validation, Text-to-Columns, Conditional Formulas, Pivot Tables.
* **GitHub:** Version Control, Project Organization, and Documentation (Markdown).

## 4. Summary of Data Quality Issues Found
Upon initial inspection, the raw dataset contained several critical errors that compromised financial reporting:
* 20 entirely duplicated order records.
* Mathematically impossible negative discount values (e.g., -0.15).
* Mismatched total `sales` figures that did not align with the quantity and unit price.
* Inconsistent capitalization and spelling in the `ship_mode` column.
* Missing geographical data in the Region and State columns.

## 5. Cleaning Steps Performed
1. **Deduplication:** Used the Remove Duplicates feature strictly on the `order_id` primary key.
2. **Text Standardization:** Applied the `=PROPER()` function to unify `ship_mode` entries.
3. **Imputation:** Filtered for blank values in Region and State and replaced them with "Not Specified".
4. **Data Type Correction:** Converted inconsistent date strings into standard Short Date formats.
5. **Formula Correction:** Applied `=MAX(0, [discount])` to zero-out negative discounts, then overwrote the total sales column with accurate calculations.

## 6. Business Rules Applied
During the cleaning process, the following business logic was enforced:
* **Revenue Rule:** Total Sales must exactly equal `Quantity * Unit_Price * (1 - Discount)`.
* **Discount Rule:** A discount cannot be less than 0%.
* **Geographic Rule:** All orders must have a designated Region/State for proper territorial reporting (nulls are unacceptable).
* **Uniqueness Rule:** An `order_id` can only exist once in the database.

## 7. Summary of Final Pivot Reports
Two primary pivot tables were generated to analyze the cleaned data:
* **Pivot Summary 1 (Sales by Region):** Analyzes total revenue and average order value across different geographic regions.
* **Pivot Summary 2 (Sales by Shipping Mode):** Evaluates which shipping methods drive the highest volume of orders and revenue.

## 8. Key Business Insights
* **Top Region:** The [Insert Region Name] region generated the highest total sales volume at $[Insert Number].
* **Shipping Preference:** [Insert Shipping Mode] is the most utilized shipping method, accounting for [Insert Percentage]% of all fulfilled orders.
* **Discount Impact:** Correcting the negative discount anomalies prevented a $[Insert estimated dollar amount or just say "significant"] artificial inflation of total reported revenue.

## 9. Assumptions and Limitations
* **Assumptions:** It was assumed that negative discount values were data entry errors (e.g., hitting the dash key accidentally) and were floored to 0% rather than deleting the entire row. Missing regions were assumed to be untracked rather than errors, hence labeled "Not Specified".
* **Limitations:** The dataset is limited to a specific time frame. Additionally, we do not have product cost data (COGS), meaning we can only report on gross revenue, not net profit margins.

## 10. Screenshots Included
Visual proof of the transformation and analysis can be found in the `screenshots/` directory:
* `raw_data_preview.png`: Showcasing the initial data inconsistencies.
* `cleaned_data_preview.png`: Showcasing the standardized, error-free dataset.
* `pivot_summary_1.png`: Visualization of the regional sales distribution.
* `pivot_summary_2.png`: Visualization of the shipping mode breakdown.
