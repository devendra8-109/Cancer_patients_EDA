# Global Cancer Patients: Exploratory & Statistical Analysis (2015-2024)

An end-to-end exploratory and inferential analysis of 50,000 cancer patient records from 10 countries/regions. The project looks at how demographics, lifestyle and environmental risk factors, cancer stage and treatment cost relate to disease severity and survival, using hypothesis tests and Random Forest models in Python.

## Dataset

- **File:** `data/global_cancer_patients_2015_2024.csv`
- **Size:** 50,000 rows, 15 columns, no missing values
- **Source:** *(add the link to where you downloaded it, and check its license)*

| Group | Columns |
|---|---|
| Demographics | Age, Gender, Country_Region, Year |
| Risk factors (0-10 scale) | Genetic_Risk, Air_Pollution, Alcohol_Use, Smoking, Obesity_Level |
| Clinical / economic | Cancer_Type, Cancer_Stage, Treatment_Cost_USD |
| Outcomes | Survival_Years, Target_Severity_Score |

## Questions Answered

1. How are patients distributed by age, gender, country, cancer type and stage?
2. Which risk factors relate to cancer severity?
3. What proportion of cancers are diagnosed early, by cancer type?
4. Which features best predict severity and survival years?
5. How does treatment cost vary across countries, genders and age groups?
6. Is higher treatment cost associated with longer survival?
7. Do higher cancer stages mean higher cost or shorter survival?
8. Does genetic risk amplify the effect of smoking on severity?

## Key Findings

- **Severity** correlates moderately with risk factors: Smoking (r ≈ 0.48), Genetic Risk (r ≈ 0.48), Air Pollution (r ≈ 0.37) and Alcohol Use (r ≈ 0.36). Age shows essentially no correlation.
- **Survival years** show near-zero correlation with every risk factor, so none of them is a meaningful linear predictor.
- **Treatment cost vs. survival:** no relationship (Pearson r = -0.0004, p = 0.92; Spearman p = 0.92).
- **Stage vs. cost and survival:** Shapiro-Wilk rejected normality in every stage, so I used Kruskal-Wallis. Neither cost (p = 0.425) nor survival (p = 0.603) differs significantly across stages.
- **Smoking × Genetic Risk interaction:** not significant (OLS interaction p = 0.628), so there is no evidence that genetic risk amplifies the effect of smoking.
- **Random Forest:** *(add your final test R² for severity and for survival years here)*. For severity, Smoking and Genetic Risk were the most important features.

> **Note on interpretation:** most variables are close to uniformly distributed and mostly uncorrelated with outcomes, which suggests the dataset may be synthetic. The results are useful for practising analysis methods, not for drawing clinical conclusions.

## Methods

- Data cleaning and descriptive statistics (Pandas, NumPy)
- Visualisation (Matplotlib, Seaborn): KDE/histograms, bar plots, heatmaps, regression plots
- Hypothesis testing (SciPy, Statsmodels): Shapiro-Wilk, Kruskal-Wallis, Pearson/Spearman correlation, OLS with interaction term
- Machine learning (Scikit-learn): Random Forest regression with `GridSearchCV`, feature importance

## Repository Structure

```
├── data/
│   └── global_cancer_patients_2015_2024.csv
├── EDA_cancer.ipynb
├── requirements.txt
└── README.md
```

## How to Run

```bash
git clone https://github.com/<your-username>/cancer-patients-eda.git
cd cancer-patients-eda
pip install -r requirements.txt
jupyter notebook EDA_cancer.ipynb
```

## Tools

Python · Pandas · NumPy · Matplotlib · Seaborn · SciPy · Statsmodels · Scikit-learn · Jupyter
