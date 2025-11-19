# Data Documentation

This directory contains all data used in the East Passyunk Accessibility Index analysis.

## Directory Structure

```
data/
├── raw/                    # Original, unmodified data
│   ├── census/            # ACS demographic data
│   ├── facilities/        # POI locations (healthcare, grocery)
│   ├── boundaries/        # Neighborhood/tract boundaries
│   └── transit/           # SEPTA transit data
└── processed/             # Cleaned, merged, analysis-ready data
```

## Data Sources

### 1. U.S. Census Bureau - American Community Survey (ACS)

**Source**: https://www.census.gov/programs-surveys/acs

**Variables Used**:
- B01001_001E: Total population
- B19013_001E: Median household income
- B25044_003E: Households without vehicles
- B01001_020E: Population 65 years and over
- C16002_001E: Limited English proficiency
- B03002_012E: Hispanic or Latino population
- B02001_003E: Black or African American population

**Geographic Level**: Census Block Group
**Year**: 2019-2023 (5-year estimates)

**How to Access**:
- Automatically downloaded using `censusdata` Python library
- API key recommended (get from: https://api.census.gov/data/key_signup.html)

### 2. OpenStreetMap (OSM)

**Source**: https://www.openstreetmap.org

**Features Extracted**:
- Healthcare facilities: `amenity=hospital`, `amenity=clinic`, `amenity=doctors`
- Grocery stores: `shop=supermarket`, `shop=grocery`, `shop=convenience`
- Pharmacies: `amenity=pharmacy`

**Method**: Retrieved using `osmnx` library
**Bounding Box**: East Passyunk neighborhood boundaries

### 3. SEPTA Transit Data

**Source**: https://www.septa.org/developer/

**Datasets**:
- Bus stops
- Subway/El stations
- Trolley stops

**Format**: GeoJSON/Shapefile

### 4. Philadelphia Neighborhood Boundaries

**Source**: OpenDataPhilly - https://opendataphilly.org

**Dataset**: Neighborhoods (Philadelphia Planning)
**Filtered to**: East Passyunk

## Data Collection Instructions

### Option 1: Run the notebook
The main notebook (`notebooks/ep_access_index.ipynb`) automatically downloads most data sources.

### Option 2: Manual download

1. **Census Data**:
   ```python
   import censusdata
   # See notebook for specific variables
   ```

2. **OSM Data**:
   ```python
   import osmnx as ox
   # Healthcare facilities
   hospitals = ox.features_from_place("East Passyunk, Philadelphia, PA", 
                                      tags={'amenity': 'hospital'})
   ```

3. **SEPTA Data**:
   - Download from SEPTA Developer Portal
   - Or use GTFS feed

## Data Processing Notes

- All spatial data projected to EPSG:3857 (Web Mercator) for consistency
- Missing values handled with median imputation for demographic variables
- Distance calculations use network distance (walking) where applicable
- Demographic data normalized to 0-1 scale for index creation

## File Naming Conventions

- Raw data: `[source]_[description]_raw.[ext]`
- Processed data: `[description]_processed.[ext]`
- Final outputs: `[neighborhood]_[metric]_[date].[ext]`

Example: `east_passyunk_accessibility_index_2025.geojson`

## Data Size Notes

⚠️ Large files (>100MB) are excluded from git repository via `.gitignore`

**Approximate sizes**:
- Census block groups (Philadelphia): ~15 MB
- OSM features: ~5 MB
- SEPTA transit: ~10 MB

## Citation

If using this data, please cite:

```
U.S. Census Bureau (2023). American Community Survey 5-Year Estimates.
Retrieved from https://www.census.gov/programs-surveys/acs

OpenStreetMap contributors (2025). Retrieved from https://www.openstreetmap.org

SEPTA (2025). General Transit Feed Specification (GTFS) Data.
Retrieved from https://www.septa.org/developer/
```

## Questions?

For questions about data sources or access, contact:
- Alex Stauf - [your email]
- Jill Kalman - [your email]

---

*Last updated: November 2025*
