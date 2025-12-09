# Data Sources

This project integrates OpenStreetMap (OSM) features, Census/ACS indicators, NDVI-based greenness, and administrative boundaries to construct the mobility, land use, environmental, and social indices.

---

## 1. OSMnx Features

Used for mobility and proximity scoring:

- Street network (sidewalks, bike lanes, curbs)
- Points of interest (health services, social services, parks)

### OSM Tags Used

```python
parks = {'leisure': ['park','playground','dog_park','recreation_ground']}
health = {'amenity':['hospital','clinic','pharmacy','dentist','nursing_home']}
services = {'amenity':['post_office','library','police','social_facility','fire_station','childcare']}
```

---

## 2. Census / ACS Indicators

Census variables were aggregated to neighborhood boundaries and feed into the **Social Score**.

### Social Vulnerability Measures

- Disability rate *(inverted)*
- Age 65+ rate *(inverted)*
- Walk-to-work mode share

---

## 3. NDVI (NAIP Imagery)

- Derived from NAIP 2019 & 2022  
- Used to compute greenness and canopy indicators  
- Supports the **Environmental Score**

---

## 4. Philadelphia Neighborhood Boundaries / City Limits

Source:  
https://opendataphilly.org/datasets/philadelphia-neighborhoods/  
https://opendataphilly.org/datasets/city-limits/

Used for spatial aggregation, mapping, and joining all final outputs.
