# Mobility Score Documentation

## Overview 
The Mobility Score evaluates neighborhood access to transportation infrastructure and options, built from three neighboehood-level indicators:

1. **Bike Lane Density** (higher = more bike-accessible streets)
2. **Sidewalk Coverage** (higher = more pedestrian-friendly streets)
3. **Curb-cartway Density (Inverted)** (lower = fewer curb cuts, better pedestrian safety)

Each indicator is computed as a density measure (length of infrastructure per unit area), normalized to a 0–1 scale, and averaged to produce a final mobility score per neighborhood. 

---

## Data Sources

- ### OpenDataPhilly 
Curbs and Cartways datasets
Bike Network dataset

- ### Census Tracts 2021 
Census tract shapefiles for spatial joins

- ### OSMnx Street Network
Load street network data for Philadelphia using OSMnx library
Also, accessed the "footway" network type for sidewalk extraction

```python
philly = ox.geocode_to_gdf("Philadelphia, PA")
```
and Amenity data for proximity analysis
```python
amenities = ox.features_from_place("Philadelphia, PA", tags={"amenity": True})
```

---
## Methodology

1. **Bike Lane Density Index**

   From OpenData Philly's Bike Network dataset, we calculated the total length of bike lanes within tracts boundary using spatial joins. Then we aggregated to neighborhood level and computed bike lane density as:
   
   FORMULA: Bike Lane Density = (total bikelane length) / (neighborhood area)

   Normalized to 0–1 scale.

   ---

2. **Sidewalk Continuity Index**

    Sidewalk networks were extracted from OSMnx street network data and combined with OpenDataPhilly sidewalk data. We calculated total sidewalk length per tract, aggregated to neighborhood level, and computed sidewalk density as:

    Sidewalk Density = 1 - (# of sidewalk gaps) / (total sidewalks)

    Normalized to 0–1 scale.

    ---

3. **Curb-Cartway Density Index (Inverted)**
    
    Using OpenDataPhilly's Curb and Cartway datasets, we calculated total curb cuts per tract, aggregated to neighborhood level, and computed curb-cartway density as:

    Curb-Cartway Density = (total curb cuts) / (neighborhood area)

    This measure was inverted (1 - normalized value) so that lower curb density yields a higher score, indicating better pedestrian safety.

    ---

4. **Composite Mobility Score Calculation**

    Finally, we averaged the three normalized indices to compute the overall Mobility Score for each neighborhood:

    Mobility Score = (Bike Lane Density + Sidewalk Continuity + Inverted Curb-Cartway Density) / 3

---

## Visualizations 

Maps and histograms were created to visualize the spatial distribution of the Mobility Score and its components across Philadelphia neighborhoods.

### Mobiltiy Component Maps 

A three panel map visualizaes the spatial distribution of each mobility component:

![Mobility Component Maps](mobility_component_maps.png) (doesn't exist yet)

---

### Histogram of Mobility Score Distribution


