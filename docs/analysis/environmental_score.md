# Environmental Score 

The Environmental Score represents the quality of a neighborhood's physical and ecological environment based on three tract-level indicators:

1. Vegetation health (NDVI) 
2. Proximity to public parks - distance from each census tract centroid to the nearest park or green space 
3. Urban tree canopy coverage - estimated tree density based on citywide canopy data

Each indicator is computed at the census tract level, normalized to a 0-1 scale, and then averaged to produce the final Environmental Score for each neighborhood. Higher scores indicate better environmental quality.

---

## Data Sources

### Remote Sensing Data & Environmental Inputs
- Landsat 8 Surface Reflectance (SR) imagery from Google Earth Engine (GEE) for NDVI calculation
- Philadelphia Parks & Recreation open data for park locations (2015)
- OpenStreetMap (OSM) data for green space features 
    - Tagged as `leisure=park`, `leisure=garden`, `leisure = playground`, etc. 

More information on data sources can be found in the [Data Sources](data_sources.md) documentation.

### Boundaries 
- Philadelphia Neighborhood Boundaries from OpenDataPhilly (GeoJSON)
- Philadelphia City Limits from OpenDataPhilly (GeoJSON)
- Census Tract Boundaries for spatial joins and zonal statistics

---

## Methodology
1. **NDVI Calculation**: 
   - Landsat 8 SR imagery for summer months (June-August) is filtered for low cloud cover (<10%) using GEE.
   - NDVI is computed using the formula: **(NIR - Red) / (NIR + Red)**.
   PLACEHOLDER FOR FORMULA
   - Census tract-level mean, median, and standard deviation of NDVI values are calculated using zonal statistics.

Values were normalized to a 0-1 scale using Min-Max scaling.

NDVI_score=NDVImax​−NDVImin​NDVImean​−NDVImin​

---

2. **Proximity to Parks**:
   - The Euclidean distance from each census tract centroid to the nearest park or green space is calculated using OSM and city park data.
   - Distances are inverted and normalized so that shorter distances yield higher scores (higher = closer to parks).
  Proximity=1−dmax
	​−dmin
	​d−dmin
	​
This measure approximates access to recreational green spaces.

---

3. **Urban Tree Canopy Coverage**:
   - Tree canopy data from the Philadelphia Urban Tree Canopy Assessment is used to estimate the percentage of tree cover within each census tract.
   - Canopy percentages are normalized to a 0-1 scale (higher = more tree cover).
   Tree Density = tree county / area (sq_mi)

   Then normalized to 0-1:
   Tree_score = density - min(density) / (max(density) - min(density))
	​
---

4. **Composite Environmental Score**:
   - The three normalized indicators (NDVI, Proximity to Parks, Tree Canopy Coverage) are averaged to compute the final Environmental Score for each census tract.
   - Environmental Score = (NDVI_score + Proximity_score + Tree_score) / 3

   Scores were then aggregated to neighborhood boundaries by averaging the tract-level scores within each neighborhood polygon.

   Passyunk Square and other neighborhoods' Environmental Scores were compared to assess spatial variations in environmental quality across Philadelphia.

   ---

## Visualization

### Neighborhood-Level Environmental Score
![Alt text](data/envmaps.png)


## Interpretation

### Passyunk Square Findings
This is Passyunk's weakest score within the accessibility index. Park proximty is strong, but it lacks meaningful vegetation that could potientially contribute to a cooler, shadier environment. 

### Citywide Patterns
South Philly at large is quite barren of trees and green vegetation, so it's not too out of the ordinary for Passyunk. However, compared to North and West Philly, it falls on the lower range of scores. There is an interesting dichotomy happening because in most metropolitcan landscapes, the most trees and green space can be found in the most upwardly mobile or economically thriving spaces. Yet North and West Philly both underperform economically and socially compared to its neighbors to the south. Passyunk has a median income of 94K, over 30k more than the city average. 
