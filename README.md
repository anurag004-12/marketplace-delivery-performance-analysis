# Marketplace Delivery Performance Analysis

## Overview

This project analyzes marketplace delivery performance for orders delivered in **May 2026**.

The main objective is to calculate the **On-Time Delivery Rate by courier** and identify delivery delays compared with the promised delivery time.

## Objectives

* Clean and standardize the delivery data.
* Handle duplicate order records.
* Exclude test orders and invalid records.
* Identify eligible orders delivered in May 2026.
* Calculate actual delivery time.
* Compare actual delivery time with promised delivery time.
* Calculate On-Time Delivery Rate for each courier.
* Visualize courier performance and delivery delays.

## Dataset

The dataset contains information about:

* Order ID
* Customer ID
* Order date
* Shipped date
* Delivered date
* City
* Courier
* Payment status
* Order status
* Promised delivery days
* Order value
* Test order indicator

## Data Cleaning

The following steps were performed:

1. Converted date columns into a consistent datetime format.
2. Standardized courier names such as `ShipQuick` and `shipquick`.
3. Standardized order status values.
4. Removed duplicate order records by keeping the latest `updated_at` record.
5. Excluded test orders.
6. Excluded cancelled orders and records with missing delivery dates.
7. Excluded orders with invalid promised delivery days.
8. Filtered orders delivered between **May 1 and May 31, 2026**.

## Delivery Performance Calculation

Actual transit time was calculated as:

```text
Actual Transit Days = Delivered Date - Shipped Date
```

An order is considered **On Time** when:

```text
Actual Transit Days <= Promised Days
```

Otherwise, it is considered **Late**.

Delivery delay was also calculated as:

```text
Delay Days = Actual Transit Days - Promised Days
```

Where:

* `0` = delivered exactly within the promised time
* Negative value = delivered early
* Positive value = delivered late

## Results

After data cleaning and filtering, **4 eligible orders** were available for the May 2026 analysis.

| Courier   | Eligible Orders | On-Time Orders | On-Time Rate |
| --------- | --------------: | -------------: | -----------: |
| Blue Dart |               1 |              1 |         100% |
| FastBee   |               1 |              1 |         100% |
| ShipQuick |               2 |              1 |          50% |

The results are based on a small sample, so they should be interpreted as an analysis of the provided dataset rather than a general assessment of courier performance.

## Visualizations

The analysis includes:

1. **On-Time Delivery Rate by Courier**
   Shows the percentage of eligible deliveries completed within the promised time.

2. **Delivery Delay vs Promised Time**
   Shows how many days each delivery was early, exactly on time, or late compared with the promised delivery time.

## Tools Used

* Python
* Pandas
* Matplotlib
* Google Colab
* Jupyter Notebook format (`.ipynb`)

## Files

```text
marketplace-delivery-performance-analysis/
│
├── task3.ipynb
├── task1_marketplace_delivery_sla_raw.csv
└── README.md
```





The analysis demonstrates how delivery data can be cleaned, validated, and analyzed to measure courier-level SLA performance and identify individual delivery delays.
