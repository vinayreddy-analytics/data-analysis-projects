# 💸 UPI Transactions Dashboard

### 📊 Overview
The **UPI Transactions Dashboard** is a Power BI report built using real-world UPI transaction data.  
It visualizes how digital payments vary across banks, devices, cities, and transaction types — highlighting monthly transaction patterns, currency-wise balances, and user demographics.

---

### 🧠 Project Steps

#### 1. Data Loading & Preparation
- Used **Excel Workbook** as data source.
- Loaded dataset into Power BI and opened **Power Query Editor**.
- Split the `TransactionTime` column (which contained both date and time) into two separate columns using:
  - `Transform → Split Column → By Delimiter → Space`
- Converted **Customer Account Number** and **Merchant Account Number** from *Whole Number* → *Text* to prevent exponential notation.
- Performed **data profiling** to ensure data quality:
  - No nulls, duplicates, or data type issues found.
  - Clean dataset with **20 columns and 20,000 rows**.

---

#### 2. Feature Engineering (DAX)
- Created a **calculated column** using **DAX** to categorize customers into age groups:
  ```DAX
  Age Groups = 
  IF('UPI Transactions'[Customerage] <= 25, "A1",
  IF('UPI Transactions'[Customerage] <= 35, "A2", "A3"))
* Added this field to slicers for demographic segmentation.

#### 3. Report Design (Page 1 — Monthly Transactions)

* Added 10 slicers, equally spaced and aligned (1280px width) for:

        1) Bank Name Sent
        2) Bank Name Received
        3) City
        4) Device Type
        5) Gender
        6) Age Groups
        7) Merchant Name
        8) Payment Method
        9) Purpose
        10) Transaction Type

* Created a Line Chart to show monthly transaction trends:
    * X-axis: Month
    * Y-axis: Transaction Amount
    * Filtered data for the year 2024

* Added a Currency Type slicer (GBP, EUR, INR, USD) enabling currency-specific filtering across all visuals.

#### 4. Report Design (Page 2 — Transaction Matrix)

* Duplicated Page 1 for consistent slicer layout.
* Added a Matrix Visual to represent:
    * Transaction Amount and Remaining Balance across months, cities, and currencies.
* Structure:
    * Rows → Month
    * Columns → City and Currency
    * Values → Amount, Remaining Balance

#### 5. Interactivity & UX Enhancements

Enabled Sync Slicers so that selections on Page 1 automatically reflect on Page 2.
(View → Sync Slicers → Enable across pages)

🔖 Bookmarks

Created interactive bookmark buttons to toggle between:
* Line chart and Column chart (for Amount visualization)
* Additional line and column visuals for Remaining Balances

Steps:
* Added both visuals on top of each other.
* Controlled visibility using Selection Pane.
* Created Bookmarks to switch between views.
* Inserted Bookmark Buttons (Line Chart / Column Chart) on top-right corner.
* Enabled toggle functionality with Ctrl + Click.

#### 🖼️ Dashboard Preview

##### Page 1 - Monthly Transactions


<img width="2538" height="1527" alt="Screenshot 2025-10-29 185449" src="https://github.com/user-attachments/assets/91f4632e-bbfc-41f5-89e1-3b3d6289396a" />


##### Page 2 - City & Currency Matrix

<img width="2557" height="1493" alt="Screenshot 2025-10-29 185520" src="https://github.com/user-attachments/assets/ba517f79-0fe6-4d5d-b433-7f13d51592df" />


#### 🧩 Features Summary

| Feature                   | Description                                           |
| ------------------------- | ----------------------------------------------------- |
| **10 Slicers**            | Interactive filtering by bank, device, city, and more |
| **Sync Slicers**          | Same filters apply across both pages                  |
| **Bookmarks**             | Switch between Line and Column visual styles          |
| **Matrix Table**          | Multi-dimensional currency and city analysis          |
| **Custom DAX Age Groups** | Dynamic segmentation for analysis                     |


#### 🧰 Tools & Technologies

| Tool                 | Purpose                                  |
| -------------------- | ---------------------------------------- |
| **Power BI Desktop** | Report building & visualization          |
| **Excel**            | Data source                              |
| **Power Query**      | Data cleaning & transformation           |
| **DAX**              | Calculated columns & interactivity logic |

