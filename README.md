# Thyroid Cancer Risk Analysis - Predictive Modeling

## Project Overview

A comprehensive machine learning analysis identifying key risk factors for thyroid 
cancer using statistical modeling and predictive analytics. This project addresses 
the challenge of early cancer detection through data-driven insights, analyzing 
patient demographics, lifestyle factors, and clinical measurements to build 
robust classification models.

---

## Objective

Identify demographic and lifestyle risk factors associated with thyroid cancer 
and develop predictive models to aid in early detection and risk assessment.

**Primary Research Question:** Are there specific demographic or lifestyle factors 
associated with increased thyroid cancer risk?

---

## Dataset

- **Source:** [Kaggle - Thyroid Cancer Risk Dataset](https://www.kaggle.com/datasets/mzohaibzeeshan/thyroid-cancer-risk-dataset/data)
- **Size:** 3,700+ patient records
- **Variables:** 13 features including:
  - Demographics: Age, Gender
  - Lifestyle: Smoking, Obesity
  - Clinical: Radiation Exposure, Iodine Deficiency, Family History
  - Biomarkers: TSH Level, T3 Level, T4 Level, Nodule Size
  - Outcomes: Diagnosis (Benign/Malignant), Thyroid_Cancer_Risk (Low/Medium/High)

---

## Methodology

### 1. Data Preprocessing
- Handled missing values and categorical encoding
- Created age groups and binary transformations for hormone levels
- Applied random under-sampling to address 77% class imbalance

### 2. Exploratory Data Analysis
- Distribution analysis across age groups and gender
- Chi-Square tests for categorical variable associations
- Box plots for numerical variable relationships
- Scatterplot matrices for multivariate analysis

### 3. Statistical Testing
**Chi-Square Test Results:**
| Variable | Chi-Square | p-value |
|----------|-----------|---------|
| Radiation Exposure | 1685.8 | < 2.2e-16 *** |
| Iodine Deficiency | 2085.4 | < 2.2e-16 *** |
| Family History | 4223.1 | < 2.2e-16 *** |
| Smoking | 0.15 | 0.696 |
| Obesity | 0.32 | 0.573 |
| Gender | 0.43 | 0.510 |

### 4. Predictive Models

**Binary Classification (Benign vs. Malignant):**

**Model 1 - Logistic Regression (Imbalanced Data):**
- Accuracy: 76.67%
- Issue: High sensitivity (99.19%), low specificity (2.41%)
- Bias toward majority class

**Model 2 - Logistic Regression (Balanced Data):**
- Accuracy: 69.66%
- Sensitivity: 89.44% | Specificity: 100%
- Kappa: 0.3931 (Fair agreement)
- **Significant Predictors:** Age, Nodule Size, Thyroid_Cancer_Risk (High/Low)

**Model 3 - Random Forest (Balanced Data):**
- Accuracy: 71.74%
- Sensitivity: 89.44% | Specificity: 65.04%
- Kappa: 0.4348 (Moderate agreement)
- **Top Variable Importance:** Thyroid_Cancer_Risk (High), Age, Nodule Size

**Multi-Class Classification (Low/Medium/High Risk):**

**Multinomial Logistic Regression:**
- Accuracy: 61.27%
- Kappa: 0.3637 (Fair agreement)
- Challenge: 0% sensitivity for Medium-risk category
- Strong bias toward High and Low predictions

---

## Key Findings

### Critical Risk Factors
1. **Radiation Exposure** (p < 2.2e-16) - Strongest predictor
2. **Iodine Deficiency** (p < 2.2e-16) - Highly significant
3. **Family History** (p < 2.2e-16) - Major genetic indicator

### Non-Significant Factors
- Smoking, Obesity, Diabetes, Gender showed no significant association

### Model Performance Insights
- Class imbalance severely impacted initial model performance
- Balancing improved minority class detection but reduced overall accuracy
- Random Forest showed marginal improvement over logistic regression
- Multi-class model struggled with intermediate risk categories

---

## Clinical Implications

- **Prioritize screening** for patients with radiation exposure history
- **Assess family history** as primary risk indicator
- **Monitor iodine levels** in at-risk populations
- Age and gender alone insufficient for risk stratification
- Need for improved Medium-risk category prediction

---

## 🛠️ Technologies Used

- **Language:** R
- **Packages:** 
  - Data manipulation: `dplyr`, `tidyr`
  - Visualization: `ggplot2`
  - Modeling: `caret`, `randomForest`, `nnet`
  - Reporting: `quarto` / `rmarkdown`
- **Statistical Methods:** Chi-Square tests, Logistic Regression, Multinomial Regression
- **ML Techniques:** Random Forest, Confusion Matrix analysis, Variable Importance

---

## Project Structure
```
├── data/                           # Raw dataset
├── code/                           # R Quarto analysis
├── output/                         # Final report PDF
├── proposal/                       # Project proposal
└── images/                         # Visualizations
```

---

## How to Run

1. Clone the repository:
```bash
   git clone https://github.com/yourusername/thyroid-cancer-risk-analysis.git
```

2. Install required R packages:
```r
   install.packages(c("ggplot2", "dplyr", "caret", "randomForest", "nnet"))
```

3. Open and run the Quarto file:
```r
   quarto render Thyroid_cancer_R.qmd
```

---

## Future Work

- Address Medium-risk category prediction challenges
- Explore advanced techniques (XGBoost, Neural Networks)
- External validation on independent datasets
- Feature engineering for hormone level interactions
- Cost-sensitive learning for clinical decision-making

---


## License

This project is for educational purposes.

---
