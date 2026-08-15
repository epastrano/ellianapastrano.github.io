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
---

## Project Overview

This project investigates a critical question in democratic theory: **How strongly are Political Rights and Civil Liberties associated globally, and do socioeconomic factors influence this relationship?**

#### Research Questions & Methodology

Using data from 2013-2024, I analyzed 195+ countries across Freedom House Index categories alongside World Bank economic indicators:
- **Primary predictor**: Political Rights rating (1-7 scale)
- **Economic factors**: GDP per capita, internet access, education completion rates
- **Geographic factors**: Regional classification and temporal trends
- **Response variable**: Civil Liberties status (binary: Free vs. Not Free)

#### Key Findings

**Political Rights is the dominant predictor** of Civil Liberties:
- **McFadden R² = 0.7244** — the model explains 72.4% of variance
- **Model accuracy = 91.9%** in predicting whether countries are Free or Not Free
- **p-value < 0.001** — the relationship is highly statistically significant

**Socioeconomic factors do not significantly predict Civil Liberties** after accounting for Political Rights. This challenges conventional development theory and suggests that economic growth alone cannot guarantee freedom.

**Regional patterns emerge**: Europe is significantly more likely to be Free, while Asia shows higher rates of restricted Civil Liberties, regardless of economic development.

#### Technical Approach

- **Method**: Binary Logistic Regression
- **Model**: `logit(P(Not Free)) = β₀ + β₁(PR) + β₂(GDP) + β₃(Internet) + β₄(Education) + β₅(Region) + β₆(Year)`
- **Data handling**: List deletion for missing values; Variance Inflation Factor (VIF) for multicollinearity assessment
- **Tools**: R (tidyverse, dplyr, caret, pROC, car)

#### Implications

The tight coupling between Political Rights and Civil Liberties suggests that **political reforms should take priority over economic development policies** for countries seeking to improve freedom. The analysis points to the need for qualitative, institution-focused approaches to democratic reform rather than relying on economic growth alone.
