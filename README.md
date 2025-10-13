# Toronto Urban Heat & Tree Canopy Explorer

Land surface temperature analysis showing the cooling effect of urban vegetation.  
Uses **Landsat 9 thermal data** combined with **greenspace and tree coverage analysis** to explore how vegetation impacts neighborhood temperatures across Toronto.

## Table of Contents
- [Data Processing (Python)](#data-processing-python)
- [Visualization (D3.js)](#visualization-d3js)
- [Methodology](#methodology)
  - [Temperature Calculation](#temperature-calculation)
  - [Vegetation Coverage](#vegetation-coverage)
- [Data Sources](#data-sources)
- [Requirements](#requirements)
- [Observable Notebook](#observable-notebook)
- [Features](#features)


## Data Processing (Python)

- **Satellite Data:** Landsat 9 Collection 2 Level-2 thermal band (`ST_B10`)  
- **Geospatial Data:** Toronto Open Data (neighborhoods, parks, treed areas, water)  
- **Processing Tools:** `GeoPandas` for spatial operations, `Rasterio` for satellite data  

**Analysis Methods:**
- Zonal statistics  
- Correlation analysis  
- Cooling score calculation  

## Visualization (D3.js)

- **Interactive Maps:** Temperature and vegetation coverage by neighborhood  
- **Scatter Plot:** Correlation between vegetation and temperature  
- **Neighborhood Explorer:** Click any area for detailed statistics  

## Methodology

### Temperature Calculation

1. Convert Landsat 9 thermal band (`ST_B10`) using Collection 2 scaling factors  
2. Filter pixels for reasonable temperature ranges (20.5°C – 42.7°C)  
3. Compute neighborhood-level averages using zonal statistics  

### Vegetation Coverage

- **Parks & Green Spaces:** 3,320 designated park areas  
- **Treed Areas:** 45,638 forested zones 

**Calculation Formulas:**

```text
Vegetation Coverage = (Total Vegetation Area / Neighborhood Area) * 100
```

```text
Cooling Score = (Vegetation Percentage * 0.6) + ((100 - Temperature * 3) * 0.4)
```

## Data Sources

- **Landsat 9:** USGS EarthExplorer (Collection 2 Level-2, September 19, 2025)  
- **Neighborhood Boundaries:** City of Toronto Open Data  
- **Parks & Green Spaces:** Toronto Open Data  
- **Treed Areas:** Toronto Open Data  

## Requirements
[Please find the shapefiles and Landsat raster yourself]

Install the dependencies with:

```bash
pip install geopandas rasterio pandas numpy matplotlib seaborn rasterstats
```


## Observable Notebook

**D3 visualization source code:**  
[https://observablehq.com/d/28763839f89cf8d8](https://observablehq.com/d/28763839f89cf8d8)

OR embed with iframe:
```html
<iframe width="100%" height="500" frameborder="0"
  src="https://observablehq.com/embed/28763839f89cf8d8?cell=*"></iframe>
```

## Features

- Interactive neighborhood selection  
- Dual map views for temperature and vegetation  
- Correlation analysis with scatter plot  
