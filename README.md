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

The initial dataset included an extra column `"Unnamed: 0"`, which was just a row index and held no analytical value. This column was removed. Scatter plots showed how each advertising medium relates to sales and helped identify potential outliers.

---

## 📊 Mean, Median, and Mode Analysis

We computed the mean, median, and mode for each feature and visualized them on histograms. These statistics help us understand the central tendency and the shape of each distribution.

### Observations:

- **TV**:
  - The distribution appears slightly right-skewed.
  - The close alignment of mean and median suggests a nearly symmetrical distribution.
  - The mode is slightly lower than the mean/median, indicating a few higher values pulling the mean up slightly.

- **Radio**:
  - Distribution is close to uniform or slightly left-skewed.
  - The near-equal values of mean, median, and mode suggest low skewness.
  - This balanced distribution implies radio ad spending is evenly spread across samples.

- **Newspaper**:
  - Right-skewed with some high-value outliers.
  - Mean is significantly higher than the median and mode.
  - Indicates the presence of a small number of large ad spend values that inflate the average, which can distort regression analysis if not handled properly.

- **Sales**:
  - Mild right skew.
  - Mean > Median > Mode pattern suggests the presence of some larger sales values that increase the average.
  - Sales data is slightly spread out but relatively consistent compared to other features.

---

## 🧹 Outlier Removal Using IQR (Newspaper Column)

To address skewness in the Newspaper column:

1. Calculated the Interquartile Range (IQR).
2. Identified upper outliers using the formula: `Upper Bound = Q3 + 1.5 × IQR`.
3. Removed rows exceeding this upper bound.

**Effect**: Removed only 2 rows, reducing the dataset from 200 to 198 rows. This cleaned data ensures that extreme values do not disproportionately influence the model.

---

## 📈 Variance Analysis

| Feature     | Variance  |
|-------------|-----------|
| TV          | 7263.67   |
| Radio       | 219.77    |
| Newspaper   | 415.94    |
| Sales       | 26.86     |

### Interpretation:

- **TV**: Very high variance, indicating a broad spread in ad spending across samples. Companies are investing vastly different amounts in TV ads.
- **Newspaper**: Moderate variance, but still notable. This supports the earlier observation about some companies spending heavily on newspapers.
- **Radio**: Lower variance than newspaper, suggesting a more uniform investment pattern.
- **Sales**: Lowest variance, implying that sales numbers are relatively consistent despite varying ad budgets.

This analysis helps identify which features might need normalization before model training.

---

## 📉 Standard Deviation Analysis

| Feature     | Std. Deviation |
|-------------|----------------|
| TV          | 85.44          |
| Radio       | 14.86          |
| Newspaper   | 20.45          |
| Sales       | 5.20           |

### Interpretation:

- **TV**: Highest standard deviation, confirming its wide investment spread. Could significantly influence model weight.
- **Newspaper/Radio**: Moderate dispersion. Indicates that most values lie close to their means.
- **Sales**: Tight distribution with the lowest standard deviation. Suggests stable sales performance across companies.

Understanding standard deviation is essential for deciding whether to scale or normalize data during preprocessing.

---

## 📌 Pearson Correlation

The correlation coefficient between **TV** and **Sales** is approximately **0.779**, indicating a **strong positive linear relationship**.

### Interpretation:

- As TV ad spending increases, sales tend to increase as well.
- The high correlation justifies using TV spend as a predictor in a linear regression model.
- Other features (Radio, Newspaper) may have lower correlations, which can be analyzed in future multivariate models.

---

## 📐 Linear Regression Model

We used a simple linear regression model using **TV advertising spend** as the independent variable and **Sales** as the dependent variable.

- The model is trained using the Ordinary Least Squares (OLS) method.
- Calculated Coefficients:
  - **Weight (Slope)** ≈ 0.047
  - **Bias (Intercept)** ≈ 7.03

### Interpretation:

- **Intercept (7.03)**: Baseline sales even when TV spend is zero.
- **Slope (0.047)**: For every additional $1K spent on TV advertising, sales increase by ~47 units.
- The model shows a good linear fit as visualized by the regression line, confirming that TV advertising is a strong predictor of sales.

---

## 🚀 Future Improvements

- Incorporate **Radio** and **Newspaper** features to build a **multiple linear regression** model.
- Perform **feature selection** and **dimensionality reduction** if needed.
- Explore **non-linear models** or **regularized regressions** (Ridge, Lasso) for better generalization.
- Create a **web interface** for users to input ad budgets and get sales predictions.

---

> All code, analysis, and results are documented in `project.ipynb`. This project provides a full walkthrough from data preprocessing to model interpretation for sales prediction using advertising budget data.
