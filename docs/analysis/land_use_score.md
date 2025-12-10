# Land Use/Health & Service Proximity Score

The Land Use & Health Service Score measures neighborhood access to key public health and social services built from two tract-level indicators:

1. **Proximity to Health Services**
2. **Porximity to Social Services & Civic Amenities**

Each indicator is computed using distance-to-nearest facility, normalized to a 0–1 scale, and averaged to produce a final amenity score per neighborhood.
Higher scores indicate better spatial access to essential services.

---

## Data Sources

- Health Services: OSMnx points of interest with tags:
  ```python
  health = {'healthcare':['hospital','clinic','pharmacy','dentist', 'emergency', 'nursing_home']}
  ```
- Social Services: OSMnx points of interest with tags:
  ```python
  service = {'amenity':['post_office','library','police','social_facility','fire_station','childcare']}
  ```

- Neighborhood Boundaries: Philadelphia neighborhood shapefile from OpenDataPhilly.
- Census Tracts: 2021 Census tract shapefiles for spatial joins.

---

## Methodology

