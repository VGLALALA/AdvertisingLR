# 📊 Sales Prediction Using Media Budgets

## 📌 Objective

To develop an accurate model that can be used to predict sales on the basis of the three media budgets.

---

## 🧾 Dataset Description

### Original Dataset Description (Provided by Client):

- **TV**: Advertising spend in thousands (K) of Canadian Dollars ($)
- **Radio**: Advertising spend in thousands (K) of Canadian Dollars ($)
- **Newspaper**: Advertising spend in thousands (K) of Canadian Dollars ($)
- **Sales**: Sales in thousands (K) of Canadian Dollars ($)

*Upon initial inspection, the units appeared inconsistent, as the advertising costs exceeded the reported sales figures. After confirming with the client, the unit for Sales has been revised for accuracy.*

### Updated Dataset Description (Confirmed by Client):

- **TV**: Advertising spend in thousands (K) of Canadian Dollars ($)
- **Radio**: Advertising spend in thousands (K) of Canadian Dollars ($)
- **Newspaper**: Advertising spend in thousands (K) of Canadian Dollars ($)
- **Sales**: Sales volume in thousands (K) of units

---

## 🔍 Dataset Visualization & Cleaning

- The column `"Unnamed: 0"` was determined to be an index column with no predictive value and was removed.
- Scatter plots of each feature were visualized to identify trends and outliers.

---

## 📊 Mean, Median, and Mode Analysis

- Histograms with vertical lines for **Mean** (Red), **Median** (Green), and **Mode** (Orange) were used to assess data distribution.
  
### Observations:
- **TV**: Slightly right-skewed. Mean and median closely aligned.
- **Radio**: Uniform to slightly left-skewed. All three measures close together.
- **Newspaper**: Slight right-skew. Mean higher than median/mode.
- **Sales**: Mild right skew. Mean > Median > Mode.

---

## 🧹 Outlier Removal Using IQR (Newspaper Column)

To reduce the influence of extreme values:

- IQR = Q3 - Q1 = 93.625 - 32.35 = 61.275
- Upper Bound = Q3 + 1.5 × IQR = 93.625
- Lower Bound is negative, thus ignored
- Rows with Newspaper spend > 93.625 were removed

➡ **Result**: Dataset reduced from 200 rows to **198 rows**

---

## 📈 Variance Analysis

Custom variance function was applied to understand feature dispersion.

| Feature     | Variance  |
|-------------|-----------|
| TV          | 7263.67   |
| Radio       | 219.77    |
| Newspaper   | 415.94    |
| Sales       | 26.86     |

**Interpretation:**
- TV has the highest variability.
- Newspaper has second highest, aligning with detected outliers.
- Sales has the lowest variance, indicating consistent outcomes.

---

## 📉 Standard Deviation Analysis

| Feature     | Std. Deviation |
|-------------|----------------|
| TV          | 85.44          |
| Radio       | 14.86          |
| Newspaper   | 20.45          |
| Sales       | 5.20           |

**Interpretation:**
- TV has the highest spread, again confirming ad spend volatility.
- Sales is the most stable across all entries.

---

## 📌 Pearson Correlation

Manual and built-in Pearson correlation between **TV** and **Sales**:
- Correlation Coefficient: **0.779**

➡ Strong positive correlation between TV advertising and sales.

---

## 📐 Linear Regression Model

**Model Used**: Ordinary Least Squares (OLS)

- **Dependent Variable**: Sales
- **Independent Variable**: TV Budget
- Custom OLS functions defined and compared visually

**Learned Coefficients**:
- Weight (Slope): ~0.047
- Bias (Intercept): ~7.03

➡ Visualization confirms a good fit between TV budget and sales trend.

---

## 🚀 Future Improvements

- Extend current single-variable regression to **multi-variable linear regression**
- Integrate Radio and Newspaper data into modeling
- Apply advanced models like Ridge, Lasso, or tree-based methods
- Deploy model as an interactive web-based prediction tool

---

> All code and analysis are in `project.ipynb`. This project demonstrates the foundational data exploration, preprocessing, and modeling process for sales prediction based on advertising budgets.
