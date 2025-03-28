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

- **TV**: Slight right-skew; mean and median aligned, mode slightly lower.
- **Radio**: Nearly uniform; mean ≈ median ≈ mode.
- **Newspaper**: Right-skewed; mean > median > mode, suggesting outliers.
- **Sales**: Mild right-skew; values relatively consistent with normal-like distribution.

---

## 🧹 Outlier Removal Using IQR (Newspaper Column)

- IQR applied to remove outliers only in the Newspaper column.
- Dataset reduced from 200 to 198 rows.

---

## 📈 Variance Analysis

| Feature     | Variance  |
|-------------|-----------|
| TV          | 7263.67   |
| Radio       | 219.77    |
| Newspaper   | 415.94    |
| Sales       | 26.86     |

- **TV** has high variance — diverse ad budgets.
- **Sales** is consistent across entries.

---

## 📉 Standard Deviation Analysis

| Feature     | Std. Deviation |
|-------------|----------------|
| TV          | 85.44          |
| Radio       | 14.86          |
| Newspaper   | 20.45          |
| Sales       | 5.20           |

- High for TV, lowest for Sales.

---

## 📌 Pearson Correlation

- TV vs Sales correlation ≈ 0.779
- Strong positive linear relationship

---

## 📐 Linear Regression Model

- TV as predictor
- OLS method
- Slope ≈ 0.047, Intercept ≈ 7.03
- Good visual fit

---

## 🚀 Future Improvements

- Add multivariate regression
- Explore regularization and non-linear models
- Build interactive dashboard

---

## 🔁 Gradient Descent (To Be Explored in Future)

While our current linear regression model uses the **Ordinary Least Squares (OLS)** analytical solution, another widely used optimization method is **Gradient Descent**.

### What is Gradient Descent?

Gradient Descent is an iterative algorithm used to minimize a cost function — typically Mean Squared Error (MSE) in regression tasks. It works by:

1. Starting with initial guesses for the model's parameters (weights and bias).
2. Calculating the gradient (slope of the cost function).
3. Updating the parameters in the opposite direction of the gradient to reduce error.
4. Repeating until the error converges to a minimum.

### Why Use Gradient Descent?

- Suitable for large datasets where OLS is computationally expensive.
- Enables training more complex models like neural networks.
- Allows for regularization techniques during optimization.

In future versions of this project, we plan to implement Gradient Descent to allow more scalable, dynamic, and extendable modeling strategies.

---

## 🧮 Sales Distribution Insight

Upon histogram inspection, the **Sales** feature exhibits characteristics of a **normal distribution**:

- The distribution is unimodal and bell-shaped.
- Most of the values cluster around the mean (~14), and fewer observations lie at the extremes.
- Mean, median, and mode are closely aligned.

### Why This Matters:

- Many machine learning models, including linear regression, perform better when the target variable (Sales) is normally distributed.
- A near-normal distribution supports assumptions like homoscedasticity (constant variance), which is beneficial for linear regression models.
- It reduces the need for transformations (e.g., log scaling) before training.

This supports our modeling approach and justifies the continued use of linear regression for predicting sales outcomes.
