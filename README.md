# Exploratory Data Analysis and PCA on Admissions Dataset

## Overview

This project performs Exploratory Data Analysis (EDA) and Principal Component Analysis (PCA) on a cleaned college admissions dataset. The main objectives are:

- Understand relationships between numeric features
- Detect and address multicollinearity
- Reduce dimensionality for more efficient modeling

## Files

- `eda_pca.qmd` — Main Quarto notebook for all EDA, PCA, and dimensionality reduction steps
- `eda_pca.html` — Rendered HTML report (self-contained)
- `enrollment2.xlsx` — Cleaned dataset with all non-numeric, text-based, or redundant fields (e.g., ZIP code, region, tags) removed.
  
## Data Preparation

- **Dataset:** `enrollment2.xlsx`
- **Cleaning:** All non-numeric, text-based, or redundant fields (e.g., ZIP code, region, tags) were removed.

## R Libraries Used

- `tidyverse`
- `corrplot`
- `factoextra`
- `skimr`
- `janitor`
- `readxl`, `writexl`
- `stringr`, `dplyr`, `here`, `skimr`
  
---

## Correlation Analysis

A Pearson correlation matrix was used to visualize relationships between numeric variables.

### Key Findings

- **High Correlations:**
  - Engagement metrics like total pings, URL counts, and durations had strong positive correlations (r > 0.70), suggesting redundancy.
  
- **Geographic Variables:**
  - Distance and in-state status were negatively correlated (r ≈ –0.69), confirming geographic logic.
  
- **Low Correlation with Outcome:**
  - Most engagement features showed weak correlation with the final enrollment outcome (|r| < 0.15).

- **Multicollinearity Risk:**
  - Email engagement variables showed high correlations (e.g., clicks and delivery rates), warranting dimensionality reduction.

---

## Principal Component Analysis (PCA)

PCA was applied to uncover latent patterns and reduce feature dimensionality.

### Process

- Standardized numeric features
- Computed principal components
- Visualized results using scree plots and biplots

### Interpretation

- First few principal components explain most variance.
- Redundant engagement metrics heavily influence PC1.
- Low-contribution variables identified and removed.

---

## Feature Reduction

Based on correlation and PCA loadings, the following were dropped:

- Repetitive ping and email engagement metrics
- Derived or weakly contributing variables (e.g., `zee_mee_engagement_score`, `distance`, etc.)

The final dataset is stored in `reduced_admits`.

---

## Output

- PCA variance explained and scree plot
- PCA biplot for variable contributions
- Reduced dataset with irrelevant features removed
- Summary statistics generated using `skimr`
  
---

## Author

**Anna Ceslavska**  
Senior at Lake Forest College  
Majors: Data Science and Economics  

