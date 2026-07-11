# Association Rule Mining: Behavioral Patterns in Office Retail

**Author:** Tantri Mizhar  
**Institution:** Institut Teknologi Sepuluh Nopember (ITS) Surabaya  
**Date:** December 2025  
**Live Code:** [View Python Script](association_rules.py) | [View Requirements](requirements.txt)

---

## 📑 Table of Contents
1. [Introduction](#1-introduction)
2. [Dataset Description](#2-dataset-description)
3. [Methodology](#3-methodology)
4. [Analysis Results](#4-analysis-results)
5. [Conclusions & Recommendations](#5-conclusions--recommendations)
6. [References](#6-references)

---

## 1. Introduction

When analyzing retail sales data, the goal isn't just to predict future revenue—it's to understand *why* customers buy what they buy. Traditional "frequently bought together" recommendations often struggle with sparsity in diverse catalogs. 

This project adopts an **attribute-value association rule mining** approach on the *Sales Forecasting* dataset. Instead of treating raw SKUs as items, we encode patterns like `"Category=Binders"`, `"Sales_bin=[300,600)"`, or `"Ship Mode=Same Day"`. This turns each order into a *behavioral profile*, uncovering decision contexts like urgency, value tier, and timing.

---

## 2. Dataset Description

The dataset (`train.csv`) covers U.S. office supply sales from 2015 to 2018. 

| Attribute | Value |
| :--- | :--- |
| **Total Rows** | 9,994 line items |
| **Unique Orders** | 4,922 (after aggregation) |
| **Time Span** | 2015–2018 |
| **Key Features** | Sales, Category, Segment, Ship Mode, Region, Order Date |

*Note: Raw product names were avoided due to extreme sparsity. Instead, items were grouped semantically (e.g., all binders became `"Category=Binders"`).*

---

## 3. Methodology

### 3.1 Feature Engineering & Discretization
Continuous variables were transformed into actionable bins to reduce noise:
- **Sales:** `[0,100)`, `[100,300)`, `[300,600)`, `[600+,10k]`
- **Order Date:** Extracted into `Order_Month` and `Order_Weekday`.

### 3.2 Transaction Construction
Each order was converted into a list of feature-value strings:
```python
["Sales_bin=[600+,10k]", "Segment=Corporate", "Category=Furniture", "Ship Mode=First Class"]
