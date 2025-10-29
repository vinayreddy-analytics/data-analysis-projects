# data-analysis-projects
A collection of my Power BI dashboards and exploratory data analysis (EDA) projects across different datasets.


# ElectroHub Sales Dashboard
### Dasboard Link - https://app.powerbi.com/reportEmbed?reportId=3008312f-bc9d-4a72-8325-63d6e9492cb7&autoAuth=true&ctid=9829d8fe-ff1d-47e3-b944-86a488e91b0e
*(The report contains 5 interactive pages: Overview, Top/Bottom 5 Analysis, Comparison, Interaction, and Table Visuals.)*
## Problem Statement
The purpose of this Power BI dashboard is to analyze store performance across multiple dimensions — including sales, profit, quantity, discounts, and customer segments.
This dashboard helps business stakeholders identify:

* Top and bottom-performing products.
* Sales and profit trends over time (daily, monthly, quarterly, yearly).
* Relationships between sales and profit.
* Average discount offered under various promotion categories.
* Total number of orders, city-wise sales distribution, and order-level details.

It provides an interactive, data-driven view of business performance and supports decision-making for pricing, promotions, and sales optimization.

## Steps Followed
### Data Loading and Preparation
* Step 1: Loaded the Excel dataset into Power BI Desktop containing four tables: 
    * Fact Table
    * Dim Customers
    * Dim Promotion
    * Dim Product

* Step 2: Opened Power Query Editor (Transform Data) for data cleaning and transformation.
* Step 3: Enabled data profiling:
    * Column quality, Column distribution, and Column profile options under the View tab.
    * This helped identify null, distinct, and error values across all tables.
* Step 4: Changed data types appropriately for all columns (Date, Text, Number, etc.).


### Data Cleaning & Transformation

* Found a column in one table with 100% null values ( column name Price per unit).
* Used Merge Queries to fill Null values in the Price per Unit column where i have Merged Fact Table with Dim Product using Product ID (Left Outer Join).
* #### Created new columns:

    * Total Sales: Units Sold * Price per Unit

    * Discount %: Filled using merge with Dim Promotion (Left Outer Join) → Replaced remaining nulls with 0.

    * Discount Value: Total Sales * Discount % / 100

    * Net Sales: Total Sales - Discount Value

    * Profit: 0.1 * Net Sales (Assumed 10% profit margin).

* Ensured consistent and accurate data quality before moving to the model.

### Data Modeling

* Identified Primary Keys (unique, non-null identifiers) in each dimension table.
* Identified Foreign Keys in the Fact Table (Customer ID, Promotion ID, Product ID).

#### Defined relationships:

* Fact Table[Customer ID] → Dim Customer[Customer ID]

* Fact Table[Promotion ID] → Dim Promotion[Promotion ID]

* Fact Table[Product ID] → Dim Product[Product ID]

#### Cardinalities established: All One-to-Many relationships (Dim → Fact).

* Star Schema structure created for efficiency and faster query performance.
* Verified relationships and cross-filter directions in Model View.

### Visuals and Measures Created

#### 1️⃣ Top/Bottom 5 Products by Sales / Profit / Quantity
* Created bar charts using:
    * Y-axis: Product Name (from Dim Product)
    * X-axis: Net Sales / Quantity / Profit
* Used visual-level filter → Top N = 5 → By Value = Net Sales

  <img width="2338" height="1192" alt="Top 5" src="https://github.com/user-attachments/assets/b6e50032-b39d-4cf2-8b7f-d1cb10182822" />


#### 2️⃣ Sales Trend Over Time

* Used a Line Chart:
    * X-axis: Date (with hierarchy — Year, Quarter, Month, Day)
    * Y-axis: Net Sales

* Enabled drill-down functionality for trend analysis across different periods.

#### 3️⃣ Relationship Between Sales and Profit

* Used Scatter Chart:
    * X-axis: Profit
    * Y-axis: Net Sales

* Clear linear relationship observed (as profit was defined as 10% of Net Sales).

  <img width="2459" height="1248" alt="Screenshot 2025-10-29 181704" src="https://github.com/user-attachments/assets/191b08e4-780d-492c-9086-1eec0f6871a5" />


#### 4️⃣ Compare Sales / Profit / Quantity Between Two Periods
#### Approach 1 (DAX-based)
* Created two Date Tables using 
```
DAX:
Date Table 1 = CALENDARAUTO()
Date Table 2 = CALENDARAUTO()
```
* Created slicers for both Date Tables.
* Built measure:
```
Sum of Net Sales = 
CALCULATE(
    SUM('Fact Table'[Net Sales]),
    ALL('Date Table 1'),
    USERELATIONSHIP('Date Table 2'[Date], 'Fact Table'[Date])
)
```
* Used similar approach and built measures for profit and Quantity
* Allowed users to compare any two periods dynamically using two slicers.
* Found this approach is Not recommended for larger models as it adds redundant tables.
  

  <img width="2456" height="1247" alt="Screenshot 2025-10-29 181823" src="https://github.com/user-attachments/assets/91bc8054-039f-4776-ac68-4bdb4e5392a6" />


#### Approach 2 (Interaction-based)

* Used two slicers from the same Fact Table date column.
* Added visuals under each slicer (Sales, Profit, Quantity).
* Modified visual interactions to restrict each chart to its slicer only.
* ✅ More efficient and cleaner method.

  <img width="2539" height="1466" alt="Screenshot 2025-10-29 182039" src="https://github.com/user-attachments/assets/cc92868a-d5d1-4791-819c-d062362c721a" />


#### 5️⃣ Average Discount Offered by Promotion
* Created bar chart:

    * X-axis: Promotion Name
    * Y-axis: Average Discount Percentage

#### 6️⃣ Total Number of Orders

* Created an Index Column in Fact Table named Order ID.
* Used a Card Visual to display the count of total orders.

#### 7️⃣ City-wise Sales Distribution

* Used Map Visual:

    * Location: City (from Dim Customer)
    * Value: Net Sales

#### 8️⃣ Order-level Analysis with Filters

* Used Table Visual displaying:
    * Sales, Profit, Discount, Net Sales, Units Sold, etc.

* Added Slicers for:

    * Product Name
    * Date
    * Customer Name
    * Promotion Category

* To ensure slicers interact correctly:

* Created measure:
```
SumDim = SUM('Fact Table'[Net Sales])
```
* Used “Show items when value is not blank” filter option.

 <img width="2526" height="1513" alt="Screenshot 2025-10-29 181951" src="https://github.com/user-attachments/assets/dcf07bbb-0c65-44e9-af2a-3d05c17988c6" />
 

### Data Model Overview

* Fact Table: Transaction-level data (Sales, Discounts, Profit, etc.)
#### Dimension Tables:
* Dim Product – Product details (ID, Category, Name, Price per Unit)
* Dim Customer – Customer details (ID, City, Age, Segment)
* Dim Promotion – Promotion details (ID, Type, Discount %)

#### Schema Type: Star Schema
* Cardinalities: One-to-Many relationships between each Dimension and Fact Table.

### Insights

* Top 5 Products: Drive over 40% of total sales.
* Sales Trend: Highest in Q3, with clear monthly seasonality.
* Discount Impact: Categories with >15% discounts show significantly higher Net Sales volume.
* City Insights: Top-performing cities contribute 60% of overall revenue.
* Profit Trend: Follows a linear relation with sales, indicating consistent profit margins.
* Customer Behavior: Promotions drive both quantity sold and order frequency.

### Conclusion

The ElectroHub Sales Dashboard provides a 360° view of business performance, enabling management to identify high-value products, evaluate promotion effectiveness, and compare performance across time periods.
It combines structured data modeling (star schema) with dynamic Power BI visuals to deliver actionable insights and enhance data-driven decision-making.








