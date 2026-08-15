---
title: Portland Streetlights and Crime Analysis
layout: default
modal-id: 2
date: 2026-05-01
img: portland_street_map.png
alt: Portland-Street-Light-Project
project-date: May 2026
client: Willamette University (MSDS)
category: Geospatial Analysis & Interactive Data Visualization
description: Spatial analysis of 2025 crime data in Portland, Oregon testing whether  streetlights deter crime. Used R and Shiny to wrangle datasets, conduct exploratory analysis, and build an interactive visualization tool for neighborhood-level exploration.
project-link: "https://maggie-g-willamette.shinyapps.io/502Final/"
---

### Data Wrangling & Preparation

**Data Integration:**
- Combined 3 datasets: Portland districts, 2025 Crime Reports, and City Streetlight locations
- Filtered data to focus on nighttime crimes (after dusk) most likely affected by street lighting
- Cleaned and standardized geographic coordinates for spatial analysis

**Exploratory Analysis:**
- Conducted basic EDA on crime patterns and lighting distribution
- Performed statistical tests and created graphics to determine best visualization approaches for this topic
- Analyzed correlation between nighttime crime and streetlight presence

### Technical Implementation

**Spatial Mapping:**
- Created an R map overlay displaying all reported crime locations with city streetlight locations
- Accounted for temporal factors (crimes committed after dusk only)
- Filtered to show crimes most likely affected by lighting presence

**Interactive Dashboard:**
- Built a Shiny Application allowing users to select specific Portland districts
- Displayed crime amount and type by neighborhood
- Tracked temporal patterns (time of day crimes were committed)
- Enabled neighborhood-level exploration and comparison

### Tools & Technologies

R, Shiny, Spatial Analysis, Data Visualization, Statistical Testing