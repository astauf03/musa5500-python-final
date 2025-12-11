# Passyunk Square Neighborhood Accessibility Character Map

Welcome to the Neighborhood Accessibility Character Map, a project developed for *MUSA 5500: Spatial Analytics*.  
This site documents the full analytical workflow used to build a multi-dimensional accessibility index* for Philadelphia neighborhoods, with a focus on **Passyunk Square** as a case study.

The project integrates four major accessibility domains:

- **Mobility** — walkability, bikeability, pedestrian infrastructure, transit-adjacent conditions  
- **Land Use / Amenities** — proximity to essential services such as healthcare and daily goods  
- **Environmental Quality** — vegetation health, park access, and urban tree canopy  
- **Social Conditions** — demographic and socioeconomic indicators that shape lived accessibility  

These domains are normalized, aggregated, and combined using a **weighted composite scoring system** to produce a final **Accessibility Score** for each neighborhood.

---

## What You’ll Find on This Site

Use the navigation bar above to explore each part of the project:

### **Project Overview**  
A summary of the research question, motivation, and conceptual framing of accessibility in urban environments.

### **Data Sources**  
A curated list of all spatial datasets used—OpenStreetMap, OpenDataPhilly, GEE remote sensing, Census ACS—and justification for each variable.

### **Methodology**  
Details on spatial processing, normalization, kernel distances, KDTree calculations, zonal statistics, aggregation to neighborhoods, and weighted scoring.

### **Domain Score Construction**  
Breakdowns for:
- **Mobility Score**  
- **Land Use Score**  
- **Environmental Score**  
- **Social Score**  
- **Final Accessibility Score**

Each section includes formulas, maps, and domain-specific interpretation.

### **Results & Interpretation**  
Citywide patterns, Passyunk Square’s relative performance, rank comparisons, and multi-domain insights.  
Includes:  
- Component maps  
- Composite maps  
- Distribution plots  
- Parallel coordinates comparing Top 5 neighborhoods  
- PSQ’s percentile placement  

### **Limitations**  
Reflections on data gaps, scale issues, representation limits, and opportunities for refinement.

### **Conclusion**  
What this index reveals about Philadelphia’s accessibility landscape and its implications for planning practice.

---

## 🎯 Project Purpose

This project demonstrates how **spatial analytics, remote sensing, and geoprocessing workflows** can combine to produce a meaningful, multidimensional understanding of accessibility beyond simple proximity metrics. The goal is not only to assess Passyunk Square, but to illustrate a **generalizable method** for neighborhood-scale accessibility evaluation.

---

You can now navigate the tabs above to dive deeper into each part of the analysis.
