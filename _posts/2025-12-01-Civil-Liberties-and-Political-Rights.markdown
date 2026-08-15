---
layout: default
modal-id: 1
date: 2025-12-01
img: R_project.png
alt: image-alt
project-date: Dec 2025
client: Willamette University (MSDS)
category: Statistical Analysis & Predictive Modeling
description: Logistic regression analysis examining the relationship between political rights and civil liberties across 195+ countries, using Freedom House Index data combined with World Bank economic indicators.
project-link: "https://github.com/epastrano/civil_liberties_and_political_rights"
---

## Research Question

How strongly are Political Rights and Civil Liberties associated globally, and do socioeconomic factors influence this relationship?

## Key Finding

Political Rights is the dominant predictor of Civil Liberties (R² = 0.7244, 91.9% accuracy). Socioeconomic factors do not significantly predict Civil Liberties after accounting for Political Rights, suggesting that economic growth alone cannot guarantee freedom.

## Technical Implementation

**Methodology:**
- Binary Logistic Regression modeling
- Data period: 2013-2024 across 195+ countries
- Model specification: `logit(P(Not Free)) = β₀ + β₁(PR) + β₂(GDP) + β₃(Internet) + β₄(Education) + β₅(Region) + β₆(Year)`

**Data Handling:**
- List deletion for missing values
- Variance Inflation Factor (VIF) assessment to evaluate multicollinearity
- Predictor variables: Political Rights ratings (1-7), GDP per capita, internet access, education completion rates, regional classification, and temporal trends
- Response variable: Civil Liberties status (binary: Free vs. Not Free)

**Tools & Technologies:**
R (tidyverse, dplyr, caret, pROC, car), Binary Logistic Regression, Statistical Analysis