# 📱 Google Play Store Data Analysis

### 🧾 Overview
This project focuses on performing **Exploratory Data Analysis (EDA)** and deriving meaningful business insights from the **Google Play Store dataset**.  
The goal is to understand the key factors that influence an app’s performance — such as **category**, **ratings**, **reviews**, **size**, **price**, and **installs** — and how these metrics relate to user engagement and overall success on the Play Store.

This project was completed as part of my data analytics learning journey using **Python** and various data visualization libraries.

---

## 🎯 Objectives
The main objectives of this analysis were to:

1. Explore the structure and characteristics of the Google Play Store dataset.  
2. Identify patterns between app ratings, installs, and reviews.  
3. Detect data quality issues such as missing values, duplicates, and incorrect datatypes.  
4. Understand how app category, size, and price influence popularity.  
5. Present findings through clear visualizations and insights.

---

## 🧠 Key Questions Explored
- Which app categories dominate the Play Store?
- Does app size or price affect its rating?
- What type of apps receive the highest number of installs?
- How are user ratings distributed across different categories?
- What’s the relationship between number of reviews and app popularity?

---

## 📂 Dataset Information

**Source:** Publicly available Google Play Store dataset (Kaggle).  
**Rows:** ~10,000+  
**Columns:** 13  

| Column | Description |
|:--|:--|
| `App` | Name of the application |
| `Category` | App category (e.g., Game, Productivity, Education, etc.) |
| `Rating` | Average rating out of 5 |
| `Reviews` | Number of user reviews |
| `Size` | App size (in MB or varied units) |
| `Installs` | Total number of installs |
| `Type` | Free or Paid |
| `Price` | Price in USD |
| `Content Rating` | Age group the app is targeted at |
| `Genres` | App genre |
| `Last Updated` | Date when app was last updated |
| `Current Ver` | Version number |
| `Android Ver` | Minimum Android version required |

---

## 🧹 Data Cleaning and Preparation

Performed extensive preprocessing to prepare the dataset for analysis:
1. **Handling Missing Values:**  
   - Filled or dropped missing values in `Rating`, `Size`, and `Reviews` columns.  
2. **Data Type Conversions:**  
   - Converted `Reviews`, `Installs`, and `Price` to numeric types for calculations.  
3. **Duplicates Removal:**  
   - Removed duplicate app records to maintain data consistency.  
4. **Feature Cleaning:**  
   - Cleaned symbols (`+`, `,`, `$`) from text-based numeric columns.  
5. **Categorical Encoding:**  
   - Standardized category and content rating fields for better grouping.  

---

## 📊 Exploratory Data Analysis (EDA)

EDA was performed using **Pandas**, **Matplotlib**, and **Seaborn**.

### Key Visual Insights:
- **Category Distribution:**  
  “Family” and “Game” apps are the most common, accounting for nearly 25% of total apps.  

- **Top-Rated Categories:**  
  Categories like *Education*, *Books & Reference*, and *Health & Fitness* tend to have higher ratings.  

- **App Size vs. Rating:**  
  Medium-sized apps (10–40 MB) generally have better ratings — possibly due to balanced features and performance.  

- **Free vs. Paid Apps:**  
  Paid apps are fewer but often rated slightly higher than free ones.  

- **Reviews vs. Installs:**  
  There’s a positive correlation — apps with more reviews tend to have higher installs and better visibility.

---

## 🧮 Analysis Techniques Used
- Descriptive Statistics (`mean`, `median`, `mode`, `std`)
- Correlation Analysis between numerical features
- Category-wise Aggregation using `groupby()`
- Outlier detection using boxplots
- Visualization using:
  - `matplotlib.pyplot`
  - `seaborn`
  - `pandas.DataFrame.plot()`

---

## 📈 Key Findings

1. **App Popularity:**  
   - “Communication,” “Social,” and “Entertainment” apps dominate in installs.  
2. **User Ratings:**  
   - The average app rating is around **4.2**, indicating generally positive user sentiment.  
3. **Price Impact:**  
   - Free apps attract more users, while paid apps perform better in niche categories.  
4. **App Size:**  
   - Extremely large or small apps tend to have slightly lower ratings — optimization matters.  
5. **Correlation Insight:**  
   - High correlation between reviews and installs (popular apps tend to have more reviews and downloads).

---

## 🧰 Tools and Technologies
| Tool | Purpose |
|------|----------|
| **Python** | Main programming language |
| **Pandas** | Data cleaning, manipulation, and aggregation |
| **Matplotlib / Seaborn** | Data visualization |
| **NumPy** | Numerical computation |
| **Jupyter Notebook** | Interactive analysis environment |

---

## 💡 Business Insights and Recommendations
- Developers should focus on **user engagement and retention**, as reviews are closely tied to installs.  
- Optimizing app size can positively influence user ratings.  
- **Education** and **Health** categories show potential for future app development due to strong user ratings and growth.  
- Regular updates maintain relevance and improve ratings over time.  

---

## 📎 Files Included
| File | Description |
|------|--------------|
| `Googleplaystoredata.ipynb` | Jupyter Notebook containing full EDA and visualizations |
| `README.md` | Documentation of the project |

---

## 🧑‍💻 Author
**Vinay Reddy Thudi**  
🎓 MSc Data Analysis for Business Intelligence — *University of Leicester*  
📍 Leicester, United Kingdom  

🔗 [GitHub Profile](https://github.com/vinayreddy-analytics)  
💼 [LinkedIn Profile](https://www.linkedin.com/in/vinay-reddy-thudi-491688128/)  

---

## 💬 Acknowledgment
Dataset sourced from [Kaggle - Google Play Store Apps Dataset](https://www.kaggle.com/lava18/google-play-store-apps).  
Used for educational and learning purposes only.

---

> *"Good data analysis doesn’t just find patterns, it explains why they matter."*
