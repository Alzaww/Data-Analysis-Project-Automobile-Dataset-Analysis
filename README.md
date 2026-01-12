# Automobile Dataset Analysis : Fuel Efficiency and Vehicle Characteristics

This project presents an exploratory and statistical analysis of an automobile dataset
from the late 1970s and early 1980s, with a particular focus on **fuel efficiency (MPG)**
and its relationship with vehicle mechanical characteristics.

The study combines **descriptive statistics**, **correlation analysis**, **distribution
diagnostics**, **Principal Component Analysis (PCA)**, and a **linear regression model**
to highlight the main factors influencing fuel efficiency.

The full analysis, figures, and interpretations are detailed in  
**[`report.pdf`](./report.pdf)** (recommended).

---

## Overview

- Dataset: 392 passenger vehicles
- Period: 1970–1982
- Variables:
  - Mechanical: cylinders, displacement, horsepower, weight
  - Performance: acceleration
  - Contextual: model year, country of origin
  - Target of interest: fuel efficiency (miles per gallon)
- Tools used:
  - Python (NumPy, pandas, matplotlib, seaborn, scikit-learn)
- All experiments and plots are reproducible from the provided Jupyter notebook

> The objective of this project is not to build a predictive model, but to **understand
the structure of the data and the factors associated with fuel efficiency**.

---

## Project Structure
- Practicalexam_code_final_version.ipynb # Main notebook (analysis and figures)
- automobiles.csv # Dataset
- figures/ # Generated plots
- report.pdf # Full written report
- README.md # Project descriptio


---

## Main Analyses

### Descriptive Statistics
- Global statistics and statistics by country of origin
- Identification of strong differences between American, European and Japanese vehicles
- Comparison of fuel-efficient vs non fuel-efficient vehicles (CAFE standard)

### Correlation and Pairwise Analysis
- Strong negative correlation between MPG and:
  - vehicle weight
  - displacement
  - horsepower
- Pairwise relationships confirming the central role of mechanical variables

### Distribution Analysis
- QQ-plot analysis of selected variables:
  - **Acceleration**: approximately normal-shaped
  - **Model year**: approximately uniform over the observed period
- These diagnostics help justify the statistical assumptions used later in the analysis

### Principal Component Analysis (PCA)
- Global PCA including all variables (MPG included)
- Mechanical PCA excluding contextual and derived variables
- Interpretation of PC1 as a dominant mechanical axis
- Visualization of PCA projections:
  - colored by country of origin
  - colored by fuel efficiency compliance

### Linear Regression
- Simple linear regression between:
  - fuel efficiency (MPG)
  - vehicle weight
- Results:
  - \( R^2 = 0.69 \)
  - RMSE ≈ 4.32 MPG
- This regression provides a quantitative complement to the PCA results

---

## How to Run the Project

### 1) Set up the environment
```bash
pip install numpy pandas matplotlib seaborn scikit-learn scipy

```
### 2) run the notebook
```bash
jupyter notebook Practicalexam_code_final_version.ipynb
```
All figures and results presented in the report can be reproduced directly from the
notebook.

---
## Notes

All numerical variables are standardized before PCA.

PCA is used as an exploratory tool, not for dimensionality reduction in a predictive
context.

Fuel efficiency is treated both as a variable of interest and as an interpretative axis,
depending on the analysis.

The dataset size is moderate, and conclusions should be interpreted accordingly.

---

## Author

Author

Alexis Zawada
December 2025
