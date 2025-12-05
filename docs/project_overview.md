# Project Overview

## 🎯 Motivation

Philadelphia’s neighborhoods vary widely in walkability, access to health/social services, environmental quality, and mobility infrastructure.  
This project creates a **composite accessibility index** to evaluate these conditions spatially at the neighborhood scale.

Passyunk Square was chosen as a case study because:

- It is a vibrant, mixed-use corridor with local amenities.  
- It has strong mobility infrastructure (bike lanes, sidewalks).  
- It provides a good contrast to lower-access neighborhoods.  

---

## 🧩 Research Questions

1. How accessible is Passyunk Square relative to other Philadelphia neighborhoods?  
2. Which components — mobility, land use, environmental, social — drive its score?  
3. How do different forms of access (services, parks, mobility) spatially reinforce or contradict each other?  
4. What limitations emerge from using open data (OSMnx, ACS, etc.)?

---

## 🛠️ Project Workflow

```mermaid
flowchart TD
    A[Collect Data] --> B[Preprocess + Clean]
    B --> C[Normalize Variables (0–1)]
    C --> D[Compute Component Scores]
    D --> E[Weighted Accessibility Index]
    E --> F[Visualization (Maps + Charts)]
    F --> G[Interpretation]
