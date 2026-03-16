# **Data Cleaning and Preparation**

## **Overview**

This document outlines the data cleaning and preparation steps performed on the Online Retail transaction dataset before analysis. The primary objective was to transform the raw transactional data into a consistent, reliable, and analysis-ready dataset suitable for visualization and business insights.

The cleaning process was conducted using Microsoft Excel, and the prepared dataset will be analyzed in Microsoft Power BI.

The original dataset contains over 500,000 rows of retail transactions, including product purchases, cancellations, and operational charges.

## **Initial Dataset Structure**

The raw dataset contained the following columns:

| Column      | Description                            |
| ----------- | -------------------------------------- |
| InvoiceNo   | Unique identifier for each transaction |
| StockCode   | Product identifier or SKU              |
| Description | Product name                           |
| Quantity    | Number of units purchased              |
| InvoiceDate | Date and time of transaction           |
| UnitPrice   | Price per product unit                 |
| CustomerID  | Unique identifier for each customer    |
| Country     | Customer's country                     |

## **Data Cleaning Steps**

### **1. Removal of Cancelled Transactions**

Invoices beginning with "C" indicate cancelled transactions.

> ### **Action**

Filtered the InvoiceNo column and removed rows where the invoice number starts with C.

> ### **Reason**

Cancelled orders contain negative quantities and do not represent completed sales transactions.

### **2. Handling Missing Product Descriptions**

Rows with blank values in the Description column were identified.

> ### **Action**

Filtered the Description column and removed rows with missing product names.

> ### **Reason**

A valid product description is required for product-level analysis.


### **3. Removal of Invalid Product Descriptions**

Some records contained placeholder or invalid descriptions, such as:


- `?`
- `missing`
- `damaged`
- `wet/rusty`
- `manual`
  
These rows were removed from the dataset.

> ### **Reason**

These entries represent inventory adjustments or system errors rather than real product transactions.


### **4. Removal of Operational and Service Charges**

Certain entries represented operational charges rather than product purchases.

Examples include:

| StockCode    | Description    |
| ------------ | -------------- |
| POST         | Postage        |
| DOT          | Dotcom postage |
| AMAZONFEE    | Amazon fee     |
| BANK CHARGES | Bank charges   |
| C2           | Carriage       |

> ### **Action**

These rows were removed.

> ### **Reason**

They represent operational costs rather than retail product sales, which would distort product performance analysis.

### **5. Removal of Gift Voucher Transactions**

Gift voucher stock codes were identified, including:

- `gift_0001_20`
- `gift_0001_30`
- `gift_0001_40`
- `gift_0001_50`

> ### Action
These rows were removed from the dataset.

> ### Reason
Gift vouchers represent **store credit purchases rather than actual product sales**, and including them will affect revenue and product performance analysis.

### **6. Removal of Invalid Price Records**

The UnitPrice column was reviewed for invalid values.

> ### **Action**

Rows where:

> UnitPrice ≤ 0

were removed.

> ### **Result**

Approximately 471 rows were removed.

> ### **Reason**

Zero or negative prices usually indicate data entry errors or accounting adjustments.

### **7. Removal of Negative Quantity Records**

Rows containing negative values in the Quantity column were identified.

> ### **Action**

Rows where:

> Quantity < 0

were removed.

> ### **Result**

Approximately 49 rows were removed.

> ### **Reason**

Negative quantities typically represent returns or corrections, which were excluded to focus on completed sales transactions.

### **8. Outlier Detection** 

Extreme quantity values were identified during data exploration.

Examples included unusually high purchase quantities such as:

* 80,995 units

* 74,215 units

> ### **Action**

These records were removed from the dataset.

> ### **Reason**

Such extreme values are likely data anomalies or bulk adjustments that could significantly distort sales analysis.

## **Feature Engineering**

To support time-based analysis, additional columns were derived from the InvoiceDate column.

| Column       | Description                     |
| ------------ | ------------------------------- |
| Year         | Year of transaction             |
| Month        | Month name                      |
| Month Number | Numeric representation of month |
| Day          | Day of transaction              |
| Hour         | Hour of transaction             |
| YearMonth    | Combined month and year field   |

These features enable efficient aggregation for monthly, daily, and hourly sales analysis.

## **Revenue Calculation**

A new column called **Revenue** was created.

Formula used:

> ### Revenue = Quantity × UnitPrice

This allows straightforward aggregation of sales values during analysis.

## **Handling Missing Customer IDs**

Approximately 13,000 rows contained missing CustomerID values.

> ### **Interpretation**

These records likely represent guest or anonymous purchases where customers were not registered in the system.

> ### **Action**

These rows were retained.

> ### **Reason**

Although the customer identity is unknown, the transactions still represent valid sales.

## **Final Dataset Characteristics**

After cleaning, the dataset contains:

* Valid product transactions only

* No cancelled orders

* No operational charges

* No invalid prices

* No negative quantities

* No extreme quantity outliers

The dataset is now structured, consistent, and ready for analysis.

## **Next Phase**

The cleaned dataset will be used to build an analytical dashboard in Microsoft Power BI, focusing on:

* Sales trends over time

* Product performance

* Customer purchasing patterns

* Geographic sales distribution

* Revenue insights
