# Data Sources 

## 1. Boundary & Reference Data
- **Neighborhood boundaries**  
  - Source: OpenDataPhilly  
  - Filename: philly_neighborhoods.geojson  
  - Used for: aggregation, mapping, and neighborhood-level scoring  

---

## 2. Environmental Data

- **NDVI (Vegetation Health)**  
    - Source: Google Earth Engine (Landsat 8 SR)  
    - Processing: seasonal filtering, NDVI formula, zonal statistics  
    - Normalized output column: `ndvi_score`

- **Tree Canopy (PPR 2015 Canopy Points)**  
    - Source: Philadelphia Parks & Recreation  
    - Processing: point density → normalized 0–1  
    - Output column: `tree_score` 

- **Park Proximity (OSM Parks)**  
    - Source: OpenStreetMap (`leisure=park`, `garden`, `playground`)  
    - Method: KDTree nearest-neighbor distance → inverted → score  
    - Output column: `park_proximity_score` 

- **Final environmental score column:**
    - `environmental_score = (ndvi_score + tree_score + park_proximity_score) / 3`
---

## 3. Land Use & Amenity Data
- **Healthcare locations (OSM)**  
   - Tags: hospital, clinic, pharmacy, dentist, emergency, nursing_home  
    - Method: KDTree nearest facility → score  
    - Output column: `health_proximity_score`

- **Civic & Social Services (OSM)**  
    - Tags: social_facility, post_office, library, police, fire_station, childcare  
    - Method: KDTree nearest service → score  
    - Output column: `service_proximity_score`

- **Final land-use score column:**  
    - `land_use_score = (health_proximity_score + service_proximity_score) / 2`  
   

---

## 4. Mobility & Public Realm Data
- **Sidewalk Network (OSM Footways)**  
    - Tags: highway=footway, footway=sidewalk, crossing  
    - Method: NetworkX components → gap density → normalized  
    - Output column: `sidewalk_index`

- **Cartways & Curbs (OpenDataPhilly)**  
    - Files: Curbs.geojson + Curbs_No_Cartways.geojson  
    - Method: cartway density → inverted → normalized  
    - Output column: `cartway_density_index`

- **Bike Network (OpenDataPhilly)**  
    - File: Bike_Network.geojson  
   - Method: lane density normalized  
    - Output column: `bike_index`

- **Final mobility score column:**  
    - `mobility_score = (bike_index + sidewalk_index + cartway_density_index)/3` 

---

## 5. Social Demographic Data (ACS 2022)
- Variables used:  
    - Disability rate (inverted)  
    - Elderly 65+ rate (inverted)  
    - Walk-to-work share  
- Level: census tract, aggregated to neighborhoods  
- Output column: `social_score`

---

## 6. Composite Accessibility Score
- **Weighted formula used in analysis:**

$$
\text{Accessibility Score} =
0.4 \times \text{Mobility Score} +
0.3 \times \text{Land Use Score} +
0.2 \times \text{Environmental Score} +
0.1 \times \text{Social Score}
$$


- Output column: `accessibility_score`


## 7. Quick Reference Table

| Domain | Dataset | Source | Output Column |
|--------|---------|--------|----------------|
| Boundaries | Neighborhoods | ODP | — |
| Environmental | NDVI | GEE | environmental_ndvi_score |
| Environmental | Trees | PPR | environmental_tree_score |
| Environmental | Parks | OSM | environmental_park_score |
| Land Use | Healthcare | OSM | health_proximity_score |
| Land Use | Civic services | OSM | service_proximity_score |
| Mobility | Sidewalks | OSM | mobility_sidewalk_score |
| Mobility | Cartways | ODP | mobility_cartway_score |
| Mobility | Bike lanes | ODP | mobility_bike_score |
| Social | ACS 2022 | Census | social_score |
| Composite | Weighted sum | — | accessibility_score |




