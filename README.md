# Dataset Description

## Overview

This dataset is designed for educational purposes to demonstrate the CART decision tree algorithm with manual Gini impurity calculations.

## Dataset Statistics

- **Total Records**: 8
- **Features**: 4 (2 categorical, 2 numerical, 1 boolean)
- **Target Variable**: 1 (binary classification)
- **Class Distribution**: Balanced (4 yes, 4 no)

## Features

### 1. computer (Categorical)
- **Type**: Nominal categorical
- **Values**: good, medium, poor
- **Description**: Quality rating of the computer
- **Distribution**:
  - good: 3 records (IDs: 1, 4, 7)
  - medium: 3 records (IDs: 2, 5, 8)
  - poor: 2 records (IDs: 3, 6)

### 2. income (Numerical)
- **Type**: Continuous numerical
- **Range**: 490 - 8968
- **Mean**: ~2196
- **Median**: ~710
- **Description**: Customer's income (in arbitrary units)
- **Note**: Contains one outlier (8968) to test robustness

### 3. price (Numerical)
- **Type**: Continuous numerical
- **Range**: 650 - 9006
- **Mean**: ~2757
- **Description**: Product price (in arbitrary units)
- **Note**: Contains two high-value items (8000, 9006)

### 4. student (Boolean)
- **Type**: Binary boolean
- **Values**: TRUE, FALSE
- **Description**: Whether the customer is a student
- **Distribution**:
  - TRUE: 3 records (IDs: 2, 6, 7)
  - FALSE: 5 records (IDs: 1, 3, 4, 5, 8)

## Target Variable

### BUY (Binary Classification)
- **Type**: Binary categorical
- **Values**: yes, no
- **Description**: Whether the customer purchased the product
- **Distribution**:
  - yes: 4 records (IDs: 3, 4, 5, 7)
  - no: 4 records (IDs: 1, 2, 6, 8)

## Complete Dataset

| ID | computer | income | price | student | BUY |
|----|----------|--------|-------|---------|-----|
| 1  | good     | 500    | 850   | FALSE   | no  |
| 2  | medium   | 800    | 900   | TRUE    | no  |
| 3  | poor     | 490    | 1000  | FALSE   | yes |
| 4  | good     | 700    | 9006  | FALSE   | yes |
| 5  | medium   | 8968   | 8000  | FALSE   | yes |
| 6  | poor     | 657    | 700   | TRUE    | no  |
| 7  | good     | 640    | 650   | TRUE    | yes |
| 8  | medium   | 720    | 950   | FALSE   | no  |

## Characteristics

### Why This Dataset?

1. **Small Size**: Easy to verify calculations manually
2. **Balanced Classes**: No class imbalance issues
3. **Mixed Types**: Tests handling of categorical and numerical features
4. **Outliers**: Contains high-value items to test split robustness
5. **Real-World Scenario**: Simulates a purchase decision problem

### Educational Value

- **Manual Verification**: All 8 records can be tracked through splits
- **Clear Patterns**: Obvious splits exist (e.g., price > 4250)
- **Multiple Features**: Demonstrates feature selection
- **Impure Nodes**: Shows need for multiple iterations

### Potential Splits

The dataset is designed so that:
- **Best Iteration 1 Split**: `price <= 4250` (Gini = 0.333)
- **Best Iteration 2 Split**: `income <= 645` (Gini = 0.222)
- **Final Tree Depth**: 3 levels
- **Perfect Classification**: 100% accuracy achievable

## Data Quality

- **No Missing Values**: All records complete
- **No Duplicates**: Each record is unique
- **Consistent Types**: All values match expected types
- **Logical Values**: All numbers are positive and reasonable

---

**Note**: This is a synthetic dataset created for educational purposes. The values and relationships are designed to demonstrate the CART algorithm clearly.
