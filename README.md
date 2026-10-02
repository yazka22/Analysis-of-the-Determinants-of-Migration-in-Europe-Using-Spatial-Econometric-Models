## TL;DR
Applied spatial econometric models (SAR, SEM, SDM) in R to analyze 
the determinants of migration across European regions. Found significant 
spatial spillover effects — migration in one region is strongly correlated 
with neighboring regions, and socio-economic factors have both direct 
and indirect (neighbor-driven) impacts.

![EU Migration Trends](EU%20Migration%20Trends%20(2000-2020).png)

**Stack:** R · spatialreg · GeoDa · spatial statistics · Python

##  Project Overview
This project explores the key factors influencing migration flows across European regions using spatial econometric models. We analyze regional determinants such as economic, social, and policy metrics, while accounting for spatial dependencies between neighboring regions.

##  Dataset
- **Data Source:** (e.g., Eurostat regional migration data and relevant socio-economic indicators)
- **Spatial Units:** European regions (e.g., NUTS2 level)
- **Variables:** Migration rates, GDP per capita, unemployment rate, education levels, policy indicators, etc.
- **Geospatial Data:** Region shapefiles for mapping and spatial weight matrix generation.

##  Methodology
1. **Data Preprocessing**
   - Merged socio-economic indicators with geospatial shapefiles.
   - Constructed spatial weight matrix (e.g., contiguity or distance-based).
2. **Exploratory Spatial Data Analysis (ESDA)**
   - Mapped migration rates across regions.
   - Calculated spatial autocorrelation (e.g., Moran’s I).
3. **Spatial Econometric Modeling**
   - Estimated models such as Spatial Lag Model (SAR), Spatial Error Model (SEM), or Spatial Durbin Model (SDM).
   - Interpreted spatial spillover effects using these models.
4. **Model Diagnostics & Validation**
   - Tested spatial dependencies and compared model fits.
   - Checked residual autocorrelation and consistency of results.

##  Key Findings
- Identified high-impact determinants of migration flows in European regions.
- Detected significant spatial spillovers—patterns where migration in one region correlated with neighboring regions.
- Quantified both direct and indirect (neighbor-driven) effects of socio-economic factors.

