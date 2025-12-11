# Limitations 

Despite our best efforts to create a multifaceted view of neighborhood accessibility, this analysis has several metholodological and conceptual limitations that should be considered when interpreting the results.

---

## Data Limitations

**Data Quality and Completeness Issues** 

- ***OpenStreetMap (OSM) Inconsistencies***
     
     - OSM coverage varies substantially across neighborhoods.
     - Sidewalks, bike lanes, and amenities are incompletely mapped, especially in North and West Philadelphia.
     - Some features (e.g., childcare centers, social services, private clinics) may be absent or misclassified, affecting proximity calculations.

- ***NDVI Resolution and Representativeness***
     
     - NDVI was extracted from Landsat 8, which has a 30m resolution after atmospheric correction. At this resolution, block-level vegetation differences—especially in dense rowhome neighborhoods like Passyunk Square—are smoothed out.
     - Seasonal NDVI variation wasn’t modeled, making environmental quality time-bound to a particular imagery window.

- ***Tree Canopy Data (PPR) Age***
     
     - The 2015 tree canopy dataset used is nearly a decade old.
     - Significant canopy loss and regrowth since then are not captured, likely misrepresenting real conditions.


---

## **Spatial Scale and Aggregation Issues**

- ***Tract to Neighborhood Aggregation***
     
     - Aggregating tract-level data to neighborhoods may obscure intra-neighborhood variability.
     - Some neighborhoods contain diverse tracts with varying accessibility profiles that are averaged out.
     - Walkshed or service areas might be more appropriate for certain analyses.


---

## **Methodological Simplifications**

- ***Nearest-Distance Approach***
     
     - Using straight-line (Euclidean) distances to nearest amenities ignores real-world travel paths, barriers, and street network connectivity.
     - Should consider using network-based distances in future analyses.

- ***Arbitrary Weighting of Components***
     
     - The equal weighting of components in composite scores may not reflect their true importance to accessibility.
     - Future work could explore data-driven weighting schemes or stakeholder input.

- ***Equity Considerations***
     
     - The analysis does not explicitly account for socioeconomic or demographic disparities in accessibility.
     - Future iterations should integrate equity-focused metrics to better capture differential access across populations.

---

## **Other Accessibility Dimensions Missing**

- ***Affordability and Social Access***
     
     - The analysis focuses on physical proximity but does *not* consider affordability, quality of services, or cost barries, which are critical to true accessibility.

---

## **Technial Limitations**

- ***No Sensitivity Analysis***
     
     - No robustness checks or sensitivity analyses were conducted to assess weight choices, distance thresholds, and normalization choices (min-max vs. z-score).

---

## Summary 

Overall, results should be interpreted as approximate indicators, not definitive statements about Philadelphia’s accessibility landscape. The analysis provides a useful exploratory framework, but future work would benefit from:

     - Higher-quality and more complete datasets

     - Network-based travel time measures

     - Updated environmental and canopy data

     - Integration of theory from mobility justice and urban accessibility literature

     - Equity-centered modeling

     - Temporal accessibility measures

     - Sensitivity testing of index construction