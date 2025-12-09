# Project Overview

## Motivation

Philadelphia’s neighborhoods vary widely in walkability, access to health and social services, environmental conditions, and mobility infrastructure.  
This project constructs a composite **Neighborhood Accessibility Index** to evaluate these dimensions at the neighborhood scale.

Passyunk Square serves as the primary case study because:

- It is a mixed-use neighborhood with a strong concentration of local amenities.  
- It has well-developed pedestrian and bicycle infrastructure.  
- It provides a clear contrast to neighborhoods experiencing lower levels of accessibility.  

---

## Research Questions

1. How accessible is Passyunk Square relative to other neighborhoods in Philadelphia?  
2. Which components—mobility, land use, environmental, and social—most strongly influence its overall score?  
3. How do different dimensions of accessibility (services, parks, mobility, environmental quality) align or diverge spatially?  
4. What limitations arise from relying on open datasets such as OSMnx, ACS, and NAIP imagery?

---

## Project Workflow

```mermaid
flowchart TD
    A[Collect Data] --> B[Preprocess and Clean]
    B --> C[Normalize Variables (0–1)]
    C --> D[Compute Component Scores]
    D --> E[Construct Composite Accessibility Index]
    E --> F[Visualization: Maps and Charts]
    F --> G[Interpretation and Evaluation]
