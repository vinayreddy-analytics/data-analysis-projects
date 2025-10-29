# ✈️ Flight Price Prediction — EDA & Feature Engineering

### 📊 Overview
This project focuses on **Exploratory Data Analysis (EDA)** and **Feature Engineering** on a flight price dataset.  
The goal is to analyze factors influencing flight prices, such as airline, route, duration, and number of stops, and prepare the data for predictive modeling.

---

### 🧠 Project Workflow

1. **Data Loading**
   - Loaded the flight dataset into a Jupyter Notebook.
   - Inspected data structure, columns, and missing values.

2. **Data Cleaning**
   - Converted `Date_of_Journey`, `Dep_Time`, and `Arrival_Time` columns to datetime format.
   - Handled missing values in `Total_Stops` and other categorical fields.
   - Removed irrelevant columns such as `Route` (after extracting features).

3. **Feature Engineering**
   - Extracted **day**, **month**, and **year** from journey date.
   - Created duration in minutes.
   - Encoded categorical variables:
     - **Label Encoding** for Airline
     - **One Hot Encoding** for Stops and Source/Destination

4. **EDA Insights**
   - Visualized flight prices by Airline, Stops, and Duration.
   - Observed that fewer stops generally lead to higher ticket prices.
   - Airline and time of journey significantly influence price.

---

### 🧰 Tools & Libraries
| Tool | Purpose |
|------|----------|
| **Python (Jupyter Notebook)** | Analysis environment |
| **Pandas** | Data cleaning & manipulation |
| **Matplotlib / Seaborn** | Data visualization |
| **Scikit-learn** | Encoding & preprocessing |

---

### 📎 Files
| File | Description |
|------|-------------|
| `2.0-EDA And FE Flight Price.ipynb` | Main Jupyter Notebook |
| `README.md` | Project documentation |

---

