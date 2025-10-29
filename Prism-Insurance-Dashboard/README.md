Prism-Insurance-Dashboard/README.md
# PRISM INSURANCE - Power BI Dashboard
## Overview
This Power BI project analyzes insurance data to visualize key business metrics such as premium amounts, claim distribution, policy activity, and customer segmentation.
The dashboard provides insights into claims by status, premium distribution by policy type, and active vs inactive policies, helping decision-makers assess financial performance and customer trends.

Dashboard Link : https://app.powerbi.com/reportEmbed?reportId=376dbf3f-1f26-466e-91bb-2ae28956c7dc&autoAuth=true&ctid=9829d8fe-ff1d-47e3-b944-86a488e91b0e


<img width="2559" height="1494" alt="Screenshot 2025-10-29 180746" src="https://github.com/user-attachments/assets/0e8e2b5a-677e-41a9-8c38-06088ff7e3a1" />

### 🧠 Project Steps

#### 1. Data Source & Setup
* Created a new database in SQL Server named insurancedb.
* Imported the insurance dataset into SQL Server.
* Modified data types (e.g., changed PolicyNumber from money to varchar(max) for consistency).
* Verified and cleaned column data types.

#### 2. Connecting SQL Server to Power BI

* Connected the SQL database (insurancedb) to Power BI Desktop.
* Clicked Transform Data to profile and understand the dataset.
* Reviewed column distribution, data quality, and data types.

#### 3. Data Transformation
* Added conditional columns using Power Query Editor:
    * Age Group Column
```
If Age ≤ 24 → "Young Adult"
If Age ≤ 60 → "Adult"
Else → "Elder"
```

* Active/Inactive Policy Column

```
If PolicyEndDate ≤ 10-Dec-2024 → "Inactive"
Else → "Active"
```

#### 4. Report View & Visualization

Built an interactive report with the following visuals:
| Visual             | Purpose                                                                 |
| :----------------- | :---------------------------------------------------------------------- |
| **Cards**          | Display total Premium Amount, Coverage Amount, and Claim Amount         |
| **Multi-row Card** | Show gender distribution (Male vs Female)                               |
| **Ribbon Chart**   | Visualize number of claims by Claim Status (Rejected, Settled, Pending) |
| **Bar Chart**      | Show Premium Amount by Policy Type (Travel, Health, Auto, Life, Home)   |
| **Line Chart**     | Compare Claim Amount across Age Groups (Young Adult, Adult, Elder)      |
| **Donut Chart**    | Show Active vs Inactive policies                                        |
| **Matrix Table**   | Display Claim Coverage Amount by Policy Type and Claim Status           |


#### 5. Interactivity & Advanced Features

* Slicers: Added filters for Policy Number, Claim Number, and Customer ID.
* Drill Through:
    * Created a second page with a detailed table visual.
    * Enabled drill-through on PolicyType so users can view detailed data for a selected policy.
* Row-Level Security (RLS):
    * Created roles in Power BI Desktop (Modeling → Manage Roles).
    * Set role conditions based on column filters.
    * Tested in Desktop and validated after publishing to Service.
* Dashboard in Power BI Service:
    * Published the report and created a one-page dashboard summarizing key visuals.
* Data Refresh Scheduling:
    * Configured Gateway connection for SQL Server to enable auto-refresh.

### ⚙️ Tools & Technologies

| Tool                 | Purpose                                          |
| :------------------- | :----------------------------------------------- |
| **SQL Server**       | Data storage and querying                        |
| **Power BI Desktop** | Data modeling and visualization                  |
| **Power Query**      | Data transformation                              |
| **Power BI Service** | Publishing, dashboarding, and refresh scheduling |


### 📈 Key Insights

* Travel policies generated the highest premium amounts (~2.5M).
* Majority of policies are Active (58%).
* Most claims are Rejected, indicating potential policy improvement opportunities.
* Adults account for the largest claim amount (~8.8M).

### 🧩 Additional Features
* Implemented drill-through navigation between report pages.
* Applied row-level security (RLS) to restrict data access by role.
* Prepared for sentiment analysis (Text Analytics) on customer feedback data using Power BI’s Text Analytics feature.

### 📤 Output

The final dashboard highlights:
* Policy performance metrics
* Gender-based claim patterns
* Premium & claim trends by policy type and age group
* Policy activity status distribution


