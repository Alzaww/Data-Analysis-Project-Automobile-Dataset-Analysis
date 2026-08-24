# Automobile Dataset Analysis: Fuel Efficiency and Vehicle Characteristics

This project presents an exploratory and statistical analysis of an automobile dataset from the late 1970s and early 1980s, with a particular focus on **fuel efficiency (MPG)** and its relationship with vehicle mechanical characteristics.

The study combines **descriptive statistics**, **correlation analysis**, **distribution diagnostics**, **Principal Component Analysis (PCA)** and **linear regression** to explore the structure of the dataset and identify the main factors associated with fuel efficiency.

The full analysis, figures and interpretations are available in [**`report.pdf`**](./report.pdf).

---

## Overview

- **Dataset:** 392 passenger vehicles
- **Period:** 1970–1982
- **Mechanical variables:** cylinders, displacement, horsepower, weight
- **Performance variable:** acceleration
- **Contextual variables:** model year, country of origin
- **Main variable of interest:** fuel efficiency (miles per gallon)
- **Tools:** Python, NumPy, pandas, Matplotlib, Seaborn, SciPy and scikit-learn

All analyses and plots can be reproduced from the provided Jupyter notebook.

The project primarily focuses on **exploratory data analysis and interpretation**, complemented by linear regression models to quantify and evaluate the relationship between vehicle characteristics and fuel efficiency.

---

## Project Structure

```text
.
├── Practicalexam_code_final_version.ipynb   # Main analysis notebook
├── automobiles.csv                          # Dataset
├── figures/                                 # Generated visualizations
├── report.pdf                               # Full written report
└── README.md                                # Project documentation
```

---

## Main Analyses

### Descriptive Statistics

Global descriptive statistics and country-specific statistics are used to compare American, European and Japanese vehicles.

The analysis highlights substantial differences between countries:

- Japanese vehicles have the highest average fuel efficiency (**30.45 MPG**)
- European vehicles average **27.60 MPG**
- American vehicles average **20.03 MPG**
- American vehicles are generally heavier and more powerful, with larger engine displacement
- They also exhibit greater variability in their mechanical characteristics

Fuel-efficient and non-fuel-efficient vehicles are also compared using a **24 MPG threshold** based on the CAFE standard considered in the analysis.

---

### Correlation and Pairwise Analysis

The correlation analysis reveals strong relationships between fuel efficiency and mechanical characteristics.

MPG is strongly negatively associated with:

- vehicle weight
- engine displacement
- horsepower

These mechanical variables are themselves strongly positively correlated, suggesting the existence of a common underlying mechanical structure.

Country-specific analyses show that these relationships are particularly pronounced among American vehicles, which also display greater mechanical diversity.

---

### Distribution Analysis

QQ-plots are used to investigate the distributions of selected variables:

- **Acceleration** exhibits a distribution reasonably compatible with normality
- **Model year** is approximately uniformly distributed across the observed period, while retaining the expected discrete structure

These analyses illustrate how distributional assumptions depend on the nature of each variable.

---

## Principal Component Analysis

Two complementary PCA analyses are performed.

### Global PCA

The first PCA includes mechanical characteristics, acceleration, model year and fuel efficiency.

It reveals a dominant structure in the dataset and shows how vehicle characteristics, fuel efficiency and country of origin relate within a reduced-dimensional representation.

### Mechanical PCA

A second PCA is restricted to four mechanical variables:

- cylinders
- displacement
- horsepower
- weight

The first principal component explains **more than 90% of the mechanical variance**.

The contributions to PC1 are:

| Variable | Contribution to PC1 |
|---|---:|
| Displacement | 26.22% |
| Weight | 25.03% |
| Cylinders | 24.99% |
| Horsepower | 23.76% |

The four variables contribute almost equally to PC1, which can therefore be interpreted as an **overall mechanical size and power axis**.

PC2 captures a more specific contrast and is mainly determined by:

- **Horsepower:** 70.64%
- **Cylinders:** 24.07%

It can be interpreted primarily as a contrast between **horsepower and engine configuration**.

The PCA also highlights differences between countries: American vehicles are more widely dispersed along the main mechanical axis, while European and Japanese vehicles form more compact and overlapping groups. This is consistent with the greater standard deviations observed for American mechanical characteristics in the descriptive analysis.

---

## Fuel Efficiency and CAFE Threshold

Vehicles are classified according to whether they reach a fuel-efficiency threshold of **24 MPG**.

Japanese vehicles have the highest proportion of vehicles above this threshold, followed by European vehicles, while American vehicles have the lowest.

However, the MPG distribution remains continuous around the threshold. The CAFE-based classification therefore does not represent a natural separation between two fundamentally different categories of vehicles.

The mechanical PCA leads to a similar observation: fuel-efficient vehicles tend to occupy the lighter and less powerful side of the mechanical axis, but substantial overlap remains between the two groups.

---

## Linear Regression

Two linear regression models are compared using an **80/20 train-test split**.

### Weight-only model

The first model predicts MPG using vehicle weight alone.

| Metric | Test result |
|---|---:|
| R² | 0.653 |
| RMSE | 4.21 MPG |

Vehicle weight alone therefore explains a substantial part of the variation in fuel efficiency.

### Multiple linear regression

A second model uses:

- cylinders
- displacement
- horsepower
- weight
- acceleration
- model year

| Metric | Test result |
|---|---:|
| R² | **0.794** |
| RMSE | **3.24 MPG** |

The improvement over the weight-only model shows that **fuel efficiency cannot be explained by vehicle weight alone**. Other mechanical characteristics and model year provide additional predictive information.

An Actual vs Predicted MPG analysis is also used to visualize the performance of the multivariate model on unseen test observations.

---

## Key Findings

- Fuel efficiency is strongly associated with vehicle mechanical characteristics.
- American vehicles are generally larger, heavier and more powerful than European and Japanese vehicles in this dataset.
- American vehicles also exhibit greater mechanical diversity.
- Mechanical PCA reveals a dominant size-and-power axis explaining more than 90% of mechanical variance.
- Fuel-efficient vehicles tend to correspond to lighter and less powerful mechanical configurations.
- Vehicle weight alone provides substantial predictive information about MPG.
- Combining several vehicle characteristics improves test performance from **R² = 0.653 to R² = 0.794**.

---

## How to Run

### 1. Install the dependencies

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter
```

### 2. Run the notebook

```bash
jupyter notebook Practicalexam_code_final_version.ipynb
```

The notebook reproduces the analyses and visualizations presented in the report.

---

## Notes

- Numerical variables are standardized before PCA.
- PCA is used primarily as an exploratory and interpretative tool.
- Regression performance is evaluated on a held-out test set.
- The dataset contains 392 observations, so conclusions should be interpreted in the context of its moderate sample size.

---

## Author

**Alexis Zawada**  
December 2025
