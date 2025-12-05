# Social Score

The Social Score represents a neighborhood’s demographic and mobility-related social vulnerability profile based on ACS tract-level indicators.  
The index combines three dimensions that influence how easily different population groups can access services, daily needs, and public space.

---

## Overview

The Social Score is constructed from three components:

1. **Disability Score (inverted disability rate)** – captures areas where fewer residents report disabilities.
2. **Elderly Score (inverted age 65+ rate)** – identifies tracts with a younger overall population.
3. **Walker-Commuter Score (walk-to-work rate)** – captures neighborhoods where residents rely on walking for daily travel, a proxy for both pedestrian infrastructure and proximity to destinations.

Each component is normalized to a 0–1 range and combined into a single index.

---

## Data Sources

All indicators come from the U.S. Census American Community Survey (ACS 5-year 2021).

Key tables used:

- **Disability:** `B18101`, `B18101A–I`, `C18108`  
- **Age cohorts:** `B01001` (male and female 65+ bins)
- **Commuting patterns:** `B08301`

A full list of variables is documented in the *Data Sources* page.

---

## Methodology

### **1. Disability Rate**

Disability counts across multiple ACS racial categories are summed and divided by total population:

\[
\text{disability\_rate} = 
\frac{\text{population\_with\_disability}}{\text{total\_population}}
\]

To align directionality (where *higher = better*), the value is inverted:

\[
\text{disability\_rate\_inv} = 1 - \text{disability\_rate}
\]

---

### **2. Elderly Rate (65+)**

All male and female age 65+ bins are combined:

\[
\text{age\_65\_plus\_rate} = 
\frac{\text{total\_age\_65\_plus}}{\text{total\_population}}
\]

Then inverted:

\[
\text{age\_65\_plus\_rate\_inv} = 1 - \text{age\_65\_plus\_rate}
\]

This does *not* imply older residents are a negative attribute; instead, elderly populations often require more mobility-supportive infrastructure.

---

### **3. Walk-Commuter Rate**

\[
\text{commute\_walk\_rate} = 
\frac{\text{commute\_walk}}{\text{total\_workers}}
\]

Higher values imply better pedestrian conditions or proximity to daily needs.

---

### **4. Normalization and Scoring**

All components are normalized using `MinMaxScaler` to ensure equal weighting:

```python
mobility_features = [
    'disability_rate_inv',
    'age_65_plus_rate_inv',
    'commute_walk_rate'
]

df[mobility_features] = scaler.fit_transform(df[mobility_features])
```
The final Social Score is computed as the average of the three normalized components:
\[
\text{social\_score} = \frac{\text{disability\_score} + \text{elderly\_score} + \text{walker\_commuter\_score}}{3}
\]

## Visualization