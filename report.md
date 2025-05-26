# Computational Statistics Project: House Price Analysis

## Overview

This project applies computational statistics techniques to analyze and predict house sale prices. We explore:
- Classical statistical inference
- Factorial experimental design (2^k)
- Multiple linear regression with ANOVA
- Time series analysis (ARIMA/SARIMA)

## Dataset

The dataset contains:
- 1,400+ observations
- 70+ features (numeric, categorical, ordinal)
- Key variables: SalePrice, OverallQual, GrLivArea, KitchenQual, etc.

## Methodology

### 1. Data Processing
- Selected 20+ influential variables (correlation > 0.5 with SalePrice)
- Handled missing values and categorical encoding

### 2. Classical Statistical Inference
- Descriptive statistics and histogram analysis
- Correlation matrix of quantitative variables
- Confidence intervals and t-tests (Welch's t-test for group comparisons)

### 3. Factorial Design (2^k)
- Conducted One-way ANOVA to identify significant categorical variables
- Built full factorial 2³ design with:
  - A: ExterQual (Exterior Quality)
  - B: KitchenQual (Kitchen Quality)
  - C: GrLivArea (Living Area, binarized)

### 4. Regression Modeling
Initial Model:
SalePrice ~ OverallQual + GrLivArea + TotalBsmtSF + GarageCars + A + B + C + A:B + A:C + B:C
- Adjusted R²: 0.768
- Significant interactions: A:C and B:C
Improved Model:
SalePrice ~ OverallQual + GrLivArea + TotalBsmtSF + GarageCars + B + D + E + B:D + B:E + B:D:E
  - D: Neighborhood (high/low)
  - E: BsmtQual (Basement Quality)
- Adjusted R²: still 0.768
- p-value lower for binary factors but similar results

### 5. Time Series Analysis
- Analyzed monthly price trends (2006-2010)
- Identified seasonal summer price spikes
- Best model: SARIMA(1,1,1)×(1,1,2,12)
- Generated 12-month price forecast
