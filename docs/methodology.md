# Methodology (Brief Overview)

This project constructs a multidimensional Neighborhood Accessibility Index for Philadelphia by combining four analytic domains:

- **Mobility** (sidewalks, bike lanes, curb/cartway structure)
- **Land Use & Amenities** (health and civic service proximity)
- **Environmental Quality** (NDVI, parks, tree canopy)
- **Social Conditions** (ACS demographic indicators)

Because each domain required different data sources and spatial operations, the full methodological details are documented **inside each domain’s dedicated markdown page**:

- [Mobility Score](docs/../analysis/mobility_score.md)
- [Environmental Score](docs/../analysis/environmental_score.md)
- [Land Use Score](docs/../analysis/land_use_score.md)
- [Social Score](docs/../analysis/social_score.md)
- [Accessibility Score](docs/../analysis/accessibility_score.md)

All components follow a consistent workflow:

---

## **1. Data Processing**

Spatial data from OSM, OpenDataPhilly, Census ACS, and Google Earth Engine were cleaned, reprojected, and clipped to the Philadelphia boundary.  
OSM-derived features (sidewalks, parks, amenities) were retrieved via OSMnx.

---

## **2. Metric Construction**

Each domain required a specific computation method:

- **Distances**: KDTree nearest-facility calculations  
- **Environmental Raster Stats**: NDVI zonal statistics  
- **Line Density Measures**: sidewalk, bike lane, and cartway length per neighborhood  
- **ACS-derived rates**: disability, elderly, commuting behavior  

---

## **3. Normalization**
All variables were scaled to a **0–1 MinMax range** to allow comparability:

\[
\text{score} = 
\frac{x - x_{\min}}{x_{\max} - x_{\min}}
\]

Some variables were inverted so that:

- **higher = more accessible**

---

## **4. Aggregation**
Metrics computed at the **tract level** were aggregated to **neighborhoods** using spatial joins and mean statistics.

---

## **5. Composite Scoring**
Each domain score was normalized, combined internally, and then incorporated into the final weighted index:

\[
\text{AccessibilityScore} =
0.4\,\text{Mobility} +
0.3\,\text{LandUse} +
0.2\,\text{Environmental} +
0.1\,\text{Social}
\]

---

This page provides the conceptual workflow.  
*See the analysis sections for fully detailed formulas, maps, and interpretation.*
