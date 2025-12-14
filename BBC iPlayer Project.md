# **![][image1]**

# **BBC iPlayer** 

# **Data Cleaning & Behaviour Analysis (Python)**

## **Project Overview**

This project demonstrates an **end-to-end data cleaning, validation, and analysis workflow** using a **synthetic BBC iPlayer-style dataset**.

The focus is on **transforming unclean, inconsistent raw data into a reliable, analysis-ready dataset**, then extracting **insights into customer viewing behaviour** through exploratory visualisations.

**Note:** The dataset is fully synthetic and does not contain real BBC iPlayer data.

## **Objectives**

* Clean and standardise messy real-world-style data

* Apply robust data validation techniques

* Handle missing values, duplicates, and outliers

* Prepare data for time-based and behavioural analysis

* Communicate methodology clearly and reproducibly

## **Dataset Summary**

**Input:**  
 unclean\_bbc\_iplayer\_dataset\_5k.csv (\~5,000 rows)

**Key fields:**

| Column | Description |
| ----- | ----- |
| show\_id | Unique row identifier |
| title | Programme title |
| genre | Programme genre |
| duration | Raw duration (inconsistent formats) |
| broadcast\_date | Broadcast date (multiple formats) |
| rating | Viewer rating (mixed types) |
| views | View count (mixed types, missing values) |

The dataset intentionally includes:

* Missing values (N/A, ?, empty strings)

* Inconsistent date and duration formats

* Mixed numeric and string types

* Duplicate records

* Outliers

## **Tools & Libraries**

* **Python 3**

* **pandas**

* **NumPy**

* **Matplotlib**

* **Jupyter Notebook**

## 

## **Data Cleaning & Preparation Pipeline (11 Steps)**

### **1\. Load & Inspect Raw Data**

* Preserve an untouched copy of the raw dataset

* Inspect schema, data types, and anomalies

### **2\. Normalise Missing Values**

* Standardise placeholders ("N/A", "?", empty strings) to NaN

* Generate missing-value reports per column

### **3\. Standardise Dates**

* Convert broadcast\_date to datetime

* Handle multiple date formats robustly

* Preserve raw date strings for traceability

### **4\. Parse & Standardise Duration**

* Convert inconsistent duration strings into numeric minutes

* Create duration\_minutes

* Flag implausible values

### **5\. Clean Numeric Fields**

* Convert rating and views to numeric

* Enforce domain rules:

  * Ratings ∈ \[1, 10\]

  * Views ≥ 0

* Retain raw values for auditability

### **6\. Remove Duplicates**

* Remove exact duplicates

* Remove logical duplicates using:

  * title

  * broadcast\_date

  * duration\_minutes

### **7\. Handle Missing Values Strategically**

* Drop rows missing critical fields (title, broadcast\_date, views)

* Impute:

  * Duration → median by genre

  * Rating → median by title (fallback to global median)

### **8\. Detect & Handle Outliers**

* Use the IQR method

* Cap extreme values (winsorisation) instead of dropping rows

### **9\. Data Validation**

Automated checks ensure:

* No missing critical fields

* Correct data types

* Valid value ranges

* No remaining duplicates

### **10\. Export Clean Dataset**

Save analysis-ready data as:

 bbc\_iplayer\_dataset\_cleaned.csv

### **11\. Behaviour Analysis & Visualisation**

Generate insights including:

* Total views by genre

* Viewing trends over time

* Views vs ratings

* Heatmap: genre × day-of-week

* Top N shows by monthly views

* Optional session-style analysis (with user-level data)

## **Example Insights**

* Certain genres show strong **weekend viewing patterns**

* Monthly top-performing titles highlight **seasonal trends**

* Ratings and views show **weak but interpretable correlation**

* Time-based aggregation enables release-impact analysis

📁 Project Structure  
.  
├── unclean\_bbc\_iplayer\_dataset\_5k.csv  
├── bbc\_iplayer\_dataset\_cleaned.csv  
├── bbc\_iplayer\_analysis\_notebook.ipynb  
└── README.md

## 

## 

## **Why This Project Matters**

This project demonstrates:

* Practical data cleaning skills

* Defensive programming with validation checks

* Realistic handling of messy data

* Clear analytical thinking

* Reproducible, well-documented workflows

It reflects challenges commonly encountered in **real-world analytics and data science roles**.

**Advanced Behaviour Analysis (Post-Cleaning)**

After producing a validated, analysis-ready dataset, the following analyses were conducted to extract **meaningful customer viewing behaviour patterns**.

These steps build directly on the cleaned data and demonstrate how preprocessing decisions enable reliable insights.

### **🔹 Heatmap: Genre × Day-of-Week Views**

**Objective:**  
 Identify how viewing behaviour varies by genre across different days of the week.

**Method:**

* Extract day of week from broadcast\_date

* Aggregate total views by:

  * genre

  * day\_of\_week

* Visualise results using a heatmap

**Insights Enabled:**

* Weekend vs weekday viewing differences

* Genre-specific viewing habits

* Identification of optimal release days per genre

**Value:**  
 Demonstrates time-based aggregation and categorical interaction analysis.

### **🔹 Session-Like Behaviour Analysis *(Optional Extension)***

**Objective:**  
 Explore deeper engagement patterns if user-level data is introduced.

**Additional Fields (Optional):**

* user\_id

* device

* timestamp

**Potential Analyses:**

* Session length (number of shows per user per day)

* Binge-watching behaviour

* Device-based consumption patterns

* Peak viewing hours

**Insights Enabled:**

* User engagement intensity

* Preferred viewing devices

* Daily and hourly viewing trends

**Value:**  
 Demonstrates scalability of the pipeline from content-level analysis to user-level behavioural analytics.

## **Project Outcome**

By extending the analysis beyond data cleaning, this project demonstrates:

* Strong data preprocessing foundations

* Ability to translate clean data into actionable insights

* Awareness of real-world analytics use cases

* A workflow that scales to richer, user-centric datasets

**Author**

Created as part of a data analytics portfolio project.  
 Designed to showcase data cleaning, validation, and exploratory analysis skills.

[image1]: <data:image/png;base64,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>