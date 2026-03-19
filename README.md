# 📊 Online Retail Sales Dashboard (Power BI)

## 🔍 Overview
This project presents an end-to-end data analytics workflow that transforms over 500,000 retail transactions into a clean, insight-driven Power BI dashboard.

The objective is to analyze business performance, identify key revenue drivers, and uncover customer purchasing behavior.


The workflow covers:
- Data cleaning in Excel
- Data modeling in Power BI
- Dashboard design with business-focused insights

---

## 🎯 Business Objective
To answer key business questions:
- How is revenue performing over time?
- Which products and customers drive revenue?
- When do customers purchase the most?
- Which countries generate the highest revenue?

---

## 📂 Dataset
- Source: Online Retail dataset  
- Records: ~500,000+ rows  
- Type: Transactional sales data  

### Key Columns:
- InvoiceNo
- StockCode
- Description
- Quantity
- UnitPrice
- CustomerID
- Country
- InvoiceDate

---

## 🧹 Data Cleaning (Excel)

### 1. Removed Cancelled Transactions
- Filtered InvoiceNo starting with **"C"**
- These represent returns/cancellations

---

### 2. Handled Missing Customer IDs
- ~13,000 rows without CustomerID
- Treated as **guest customers**
- Retained for revenue analysis

---

### 3. Removed Invalid Prices
- Deleted rows where:
  - UnitPrice ≤ 0
- Removed ~471 rows

---

### 4. Checked Quantity Column
- Removed negative quantities not tied to cancellations

---

### 5. Removed Non-Product Records
Filtered out StockCodes such as:
- POST, BANK CHARGES, AMAZONFEE, DOT

These are **service/operational entries**, not products

---

### 6. Cleaned Description Column
- Removed blank and irrelevant values (e.g. "missing")
- Ensured meaningful product descriptions

---

### 7. Validated Outliers
- Investigated high quantities (e.g. 80,000 units)
- Retained valid bulk transactions

---

### 8. Created New Columns
- Revenue = Quantity × UnitPrice
- Year
- Month
- Day
- Hour
- Year-Month

---

### 9. File Optimization
- Compressed Dataset for GitHub upload

---

## 📊 Power BI Development

### Data Modeling
- Imported cleaned dataset
- Verified data types
- Built DAX measures:

#### Measures:
- Total Revenue
- Total Transactions
- Average Order Value (AOV)
- Total Customers

---

## 📈 Dashboard Structure

### 🟦 Page 1: Performance Dashboard

#### KPI Cards
- Total Revenue
- Total Transactions
- Average Order Value
- Total Customers

---

#### Visuals
- Revenue Trend Over Time (Line Chart)
- Top 10 Products by Revenue (Bar Chart)
- Top 10 Countries by Revenue (Bar Chart) *(Replaced map for stability)*
- Sales Distribution by Hour (Column Chart)

---

### 🟩 Page 2: Customer Insights

- Top 10 Customers by Revenue
- Customer Purchase Behavior by Hour

---

## 🎛 Interactivity

- Slicers:
  - Country
  - Year
  - Month

- Reset Button:
  - Added slicer Reset button without affecting visual filters

---

## 🎨 Design Decisions

- Blue → Revenue
- Green → Behavioral metrics
- Minimalist layout (no clutter)
- No map visual (to avoid sign-in dependency)

---

## 🧠 Key Insights

- Revenue shows a generally positive trend with periodic fluctuations
- Revenue is highly concentrated among a few products
- A small number of customers generate most revenue
- Sales peak during mid-day hours
- A few countries, such as `The United Kingdom`, dominate overall sales performance  
---

## ⚙️ Tools Used

- Excel (Data Cleaning)
- Power BI (Modeling & Visualization)

---

## 🚀 How to Use

1. Download the `.pbix` file  
2. Open in Power BI Desktop  
3. Use slicers to explore data  
4. Use the reset button to clear filters  

---

## 📌 What This Project Demonstrates

- Handling large datasets (500k+ rows)
- Data cleaning and validation
- Business-focused dashboard design
- Use of DAX for KPIs
- Building interactive dashboards

---
## 🔧 Suggested Improvement

To further enhance data quality and analytical accuracy, the following improvement is recommended for future iterations of this project:

- **Handle Missing Customer Identifiers:**
  The `CustomerId` field contains blank or missing values, which may impact customer-level analysis.

  **Proposed Approach:**
  Replace blank or null `CustomerId` entries with a standardized label such as `"Guest"`.


### 💡 Impact
This project focus mainly on sales performance, however, Implementing this change will strengthen data integrity and provide a more complete view of customer behavior, especially when analysis focuses on customer's purchase patterns.
