# Overview
We have association rules project where we select any transactional dataset from https://www.kaggle.com/datasets or https://archive.ics.uci.edu/ml/index.php. 

The project conduct an association rule analysis, including: enerating frequent item sets and association rules for three different pairs of support and confidence thresholds, comparing the impact of changing the thresholds on the number and quality of rules, identifying the most interesting rules and their potential significance in the context of the data.

# Introduction
In today’s competitive retail landscape, understanding why customers dont buy just what they buy is critical for strategic decision-making. Traditional market basket analysis, which mines co-purchases of specific products (e.g., “Binders → Paper”), often struggles with sparsity and limited generalizability, especially in catalogs with thousands of SKUs. To address this, this study adopts an attribute-value association rule mining approach on the Sales Forecasting dataset (Kaggle: rohitsahoo/sales-forecasting), treating each order not as a list of products, but as a behavioral profile defined by semantic features, such as order value tier, shipping urgency, customer segment, and time of purchase. By doing so, we uncover high-level purchasing behaviors that directly inform bundling strategies, logistics optimization, and retention campaigns.

Association Rule Mining (ARM) is a powerful unsupervised learning technique used to uncover hidden, actionable patterns in transactional data, commonly known as Market Basket Analysis.

This approach let me uncover not just product affinities, but decision contexts: urgency, value tier, segment, and timing, all of which open doors to smarter bundling, logistics tuning, and retention strategies.

# Methodology

The analysis follows a systematic pipeline aligned with best practices in ARM:

1. Preprocessing Data
Before we analyze the data deeply, we must accomplish preprocessing data, such as handling missing values, duplicates, outliers, or noise.
2. Transaction Construction
["Sales_bin=[100,300)", "Order_Weekday=Monday", "Segment=Corporate", "Category=Technology", ...]
3. Binary encoding
Using mlxtend.preprocessing.TransactionEncoder, transactions are converted into a binary matrix (orders × items), where 1 = presence, 0 = absence.
4. Apriori Algorithm
Using the mlxtend library, we applied the Apriori algorithm to the binary-encoded transaction matrix, systematically evaluating three threshold configurations to balance coverage and signal strength:

- Strict (support ≥ 0.05, confidence ≥ 0.70), designed for high certainty, high-frequency rules, yielded zero rules—indicating that real world purchasing behaviors in this dataset are too diverse to meet such conservative criteria.
- Balanced (support ≥ 0.03, confidence ≥ 0.60), selected as the primary configuration, produced 24 high quality rules with an average lift of 1.35 and a maximum lift of 1.86, demonstrating strong, non random associations.
- Exploratory (support ≥ 0.01, confidence ≥ 0.50), while generating 342 rules, showed a marked decline in average lift (1.15), suggesting increased noise, though it did reveal high, outlier rules (e.g., lift = 2.10).
All rules were post-filtered to retain only those with lift > 1.0, ensuring that only positively associated patterns—those occurring more frequently together than expected by chance, were considered.

Let's try to execute this project

# Dataset Description

The dataset (train.csv, 9,994 rows) resembles the well-known Superstore schema and covers U.S. office supply sales from 2015 to 2018. After grouping by Order ID, We worked with 4,922 unique transactions, each containing:

Sales total per order (summed across line items)
Categorical metadata: Category (e.g., Binders, Furniture, Technology), Segment (Consumer/Corporate/Home Office), Ship Mode, Region, and Order Date
One row was missing Postal Code (Burlington, VT), which I manually imputed as 5401 after verifying it matched the city/state combination, this is standard practice for small-scale imputation when domain knowledge supports it.

