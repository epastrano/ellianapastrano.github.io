---
layout: default
modal-id: 2
date: 2026-05-01
img: portland_street_map.png
alt: Portland-Street-Light-Project
project-date: May 2026
client: Willamette University (MSDS)
category: Geospatial Analysis & Interactive Data Visualization
description: Spatial analysis of 2025 crime data in Porland, Oregon testing whether  streetlights deter crime. This includes an interactive Shiny dashboard for neighborhood-level exploration.
project-link: https://maggie-g-willamette.shinyapps.io/502Final/
---

## Project Overview

**Do streetlights make walking home at night safer?** This project analyzes Portland's 2025 crime and streetlight data to test whether street lighting deters crime, or if crimes cluster near lights for other reasons entirely.

## Research Questions & Methodology

#### Key Question
Do streetlights deter targeted crime categories affecting pedestrians traveling at night, or is lighting a proxy for other urban factors?

#### Data & Approach
- **Data sources**: 2025 Portland crime reports (15,331 total; 6,242 night crimes) + open streetlight inventory
- **Spatial transformation**: Converted to meter distance; imported street network from Portland Open Data to ensure accurate crime/light location analysis
- **Dynamic lighting threshold**: Each streetlight's effective range calculated based on lumens: `(20 × √(Lumen / 4000)) + 20` meters
- **Statistical method**: Chi-square testing of crime frequency in lit vs. unlit areas
- **Density analysis**: Crime per km² in lit vs. unlit zones
- **Control testing**: Reanalyzed in urban-only districts (Pearl District, Old Town, Downtown) to control for urban density variation

### Key Findings

#### Surprising Result: Crimes ARE Near Lights (But Not Why You'd Think)

**Total Portland Area (31.17 km² of streets):**
- 74.4% of street area was lit
- **91.9% of 6,242 night crimes occurred in lit areas**
- Chi-square test: **χ² = 1003.1, p < 0.0001** (highly significant)
- Crime density: **247.3 crimes/km² in lit areas** vs. 63.4 in unlit areas

**Urban Districts Only (4.53 km²):**
- 85.7% of streets lit
- **98.0% of 1,820 crimes in lit areas**
- Chi-square test: **χ² = 226.63, p < 0.0001** (highly significant)
- Crime density: **459.8 crimes/km² in lit areas** vs. 55.38 in unlit areas

#### Theories

1. **Streetlights deter crime** — *Cannot be ruled out*, but would require before/after streetlight placement data
2. **Streetlights are a proxy for urban density** — **STRONGLY SUPPORTED.** Even when controlling for highly urban districts, the pattern held
3. **Urban density is the lurking variable** — **MOST LIKELY.** Lights mark high-activity zones, not safer zones

### Technical Implementation

- **Data cleaning & spatial joining**: R (sf, sp packages)
- **Spatial analysis**: Dynamic buffer calculations, density mapping, chi-square testing
- **Interactive dashboard**: Shiny app allowing users to explore results by Portland neighborhood and crime type
- **Visualization**: Interactive maps, crime density comparisons, neighborhood-level breakdowns

#### Conclusions

**Bottom line:** Statistically, you're not safer walking where there are more streetlights. Crimes cluster near lights because lights mark busy urban centers, not because lights cause or prevent crime.

**Practical takeaway:** 
- Walk home in the dark. Walk home in the light. Your safety depends more on the neighborhood's inherent activity level than on street lighting.
- Future research should use temporal analysis (before/after streetlight placement) and account for urban density as a confounding variable.

