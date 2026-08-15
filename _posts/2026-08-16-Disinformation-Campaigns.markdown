---
layout: default
modal-id: 3
date: 2026-08-14
img: disinformation_score.png
alt: Disinformation-Project
project-date: August 2026
client: Willamette University (MSDS Capstone)
category: Predictive Modeling & Cross-National Analysis
description: Machine learning analysis predicting disinformation campaign intensity using global news media characteristics and expert-coded indicators across 179 countries, 2015-2025.
project-link: "https://wu-msds-capstones.github.io/project-writeup-maggie-elliana/)"
---

## Project Overview

**Can media environment characteristics predict disinformation risk?** This capstone examines whether a country's news landscape—its thematic focus, tone, and content patterns—can forecast the intensity of domestic and foreign disinformation campaigns using large-scale global data.

## Research Questions & Methodology

### Core Question
Can characteristics of a country's media environment be associated with the intensity of foreign and domestic disinformation campaigns?

### Theoretical Foundation
Prior research emphasizes that disinformation thrives not just through isolated false claims, but through the broader structure of media ecosystems. State and non-state actors exploit existing social and political divisions rather than creating new ones. Despite this ecosystem-level theory, most detection work focuses narrowly on individual articles or posts. **This project bridges that gap.**

### Data Sources & Scale

**GDELT (Global Data on Events, Location, and Tone)**
- Continuously updated archive of global news (broadcast, print, web)
- ~2.5 trillion observations per year
- 2015-2025 timeframe (3,148 country-year observations initially)
- Captures: article tone, themes, actors, events across languages and countries

**Digital Society Project (DSP)**
- Expert-coded cross-national measures of disinformation campaigns
- 179 countries, 2015-2025
- Distinguishes foreign vs. domestic sources
- 33 indicators of freedoms in internet and politics

### Feature Engineering
**Country-Year Level Aggregation:**
- 19 summary statistics per country-year
- 11 thematic groups derived from disinformation literature:
  - Social Unrest, Identity Division, Military Conflict
  - Governance Trust, Information Environment, Economic Instability
  - Democratic Elections, Public Health, Climate, Migration, Cybersecurity
- Final feature vector: **174 variables** from 2,591 observations

**Transformations:**
- Shrunk theme metrics relative to baseline to maintain social context
- Log/Center Log Ratio transformations to account for data skew
- Created domestic & foreign disinformation scores by averaging 4 DSP indicators each

## Key Findings

### Model Performance

**Random Forest (Group K-Fold Cross-Validation, 5 folds holding out entire countries):**
- **R² = 0.345** — Explains 34.5% of variance on unseen countries
- This is substantively meaningful for cross-national, observational social science data

**XGBoost Models:**
- **Replication model:** R² = 0.342, RMSE = 1.029, MAE = 0.811
- **Temporal change model:** R² = 0.347, RMSE = 1.025, MAE = 0.806

### Feature Importance

**Most predictive themes:**
1. **Social identity & division** (especially for temporal changes)
2. **Military conflict**
3. **Democratic elections**
4. **Information environment**
5. **Economic instability**
6. **Cybersecurity**

**Tone indicators that matter:**
- Relative theme share
- Strong negativity prevalence
- Tone variance

**What surprisingly didn't work:**
- Sentiment polarity (too common in legitimate political coverage)
- Social media embeddings (operate on different timescales)
- Immigration, climate, governance trust themes (nation-specific relationships)

### Domestic vs. Foreign Campaigns

**Key insight:** Domestic campaigns were significantly easier to predict (R² ~0.35) than foreign campaigns (much lower performance).

**Why?** Domestic campaigns embed in existing political institutions and media patterns. Foreign campaigns intentionally obscure origins and adapt tactically to local contexts, introducing heterogeneity that resists generalization.

## Technical Implementation

**Data Processing:**
- SQL queries through Google BigQuery for GDELT ingestion
- Multilayered table design for aggregate transformation
- Feature shrinking and CLR transformation for skewed distributions

**Modeling Approaches:**
- Random Forest for dimensionality reduction & baseline prediction
- XGBoost with random search + grid search hyperparameter tuning
- Group K-Fold cross-validation (holding out entire countries)

**Tools:** Python, scikit-learn, XGBoost, pandas, BigQuery

## Implications & Conclusions

### What Works
Thematic content patterns—particularly the presence of discussions about identity, conflict, elections, and governance—are stronger predictors of disinformation intensity than sentiment or polarity alone. This supports theory that disinformation campaigns succeed by **exploiting existing fault lines**, not inventing new narratives.

### What Doesn't Transfer
Features effective for article-level detection (polarity, sentiment) don't necessarily work at the environment level. This suggests **different mechanisms operate at different scales of analysis**.

### Generalizability
Models show cross-national predictive power without regional tuning, indicating global consistency in media environment–disinformation relationships. However, richer country-specific features could improve performance.

### Future Work
- **Neural networks** for greater model complexity
- **Temporal modeling** to capture dynamic relationships
- **Multi-source validation** beyond DSP expert coding
- **Expanded computational resources** for full GDELT coverage
- **More granular thematic categorization**

## Project Impact

This work provides a **preliminary framework for predicting disinformation risk** based on observable media patterns—useful for:
- Everyday citizens understanding their media environment
- Policymakers and media personnel designing interventions
- Researchers studying the structural causes of disinformation vulnerability

The finding that media *themes* matter more than *sentiment* reframes how we should think about disinformation: it's not about emotional manipulation alone, but about the underlying social and political fault lines a country is actively discussing.