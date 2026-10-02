# Analysis of the Determinants of Migration in Europe Using Spatial Econometric Models

---

## TL;DR

Applied **spatial econometric models** (OLS, Spatial Lag, Spatial Error) to analyze the determinants of net migration across **260 European NUTS-2 regions**. Found strong **spatial autocorrelation** (Moran's I = 0.372, p < 0.001) — migration in one region is significantly influenced by neighboring regions. **Economic factors (GDP, wages, unemployment)** are the dominant drivers, while social and infrastructure variables are largely insignificant. The **Spatial Error Model** outperforms OLS (R² 0.375 vs. 0.215, lower AIC), confirming that ignoring spatial dependence leads to biased estimates.

![Local Moran's I Cluster Map](Local%20Moran%20I%20Cluster%20Map.png)

*Spatial clusters of net migration across European NUTS-2 regions. Red — High-High clusters (Western/Northern Europe). Blue — Low-Low clusters (Eastern/Southeastern Europe). Source: own processing in GeoDa.*

---

## Research Question

**What socio-economic factors drive migration flows between European regions, and how does spatial dependence between neighboring regions shape these flows?**

The study combines **push-pull migration theory** with **spatial econometrics** to test whether regional migration patterns can be explained by economic, demographic, and social variables — while explicitly modeling spatial spillovers.

---

## Data

| Aspect | Detail |
|---|---|
| **Source** | Eurostat, NUTS-2 level |
| **Year** | 2021 |
| **Observations** | 260 European regions |
| **Variables** | 11 (1 dependent, 10 independent) |
| **Spatial weights** | Rook contiguity, order 2 (min. 1 neighbor, max 19, median 10) |

**Dependent variable:**
- `MigNB` — crude net migration rate (per 1,000 inhabitants)

**Independent variables:**
- **Economic:** GDP per capita, Employee salary, Unemployment rate
- **Demographic:** Urbanization degree, Population density
- **Social:** Education level, Poverty risk rate, Crime rate, Private housing
- **Health:** Infant mortality rate, Hospital beds per capita

GDP and salary are highly correlated (r = 0.86), so they are included **alternately** in the models to avoid multicollinearity.

---

## Methodology

1. **Exploratory Data Analysis** — distribution maps, boxplots, outlier detection, log-transformation of GDP.
2. **Global spatial autocorrelation** — Moran's I with 999 permutations.
3. **Local spatial autocorrelation** — Local Moran's I, cluster maps (High-High, Low-Low, outliers).
4. **Baseline OLS regression** — to establish non-spatial benchmarks.
5. **Spatial models:**
   - **Spatial Lag Model (SAR)** — captures spillover effects through the dependent variable.
   - **Spatial Error Model (SEM)** — captures spatial autocorrelation in residuals.
6. **Model selection** — Lagrange Multiplier tests (LM lag, LM error, robust versions), Likelihood Ratio test, AIC.

---

## Key Results

### 1. Strong spatial autocorrelation

| Variable | Moran's I | Pseudo p-value | Z-value |
|---|---|---|---|
| Net migration (MigNB) | **0.372** | 0.001 | 11.51 |
| Salary | 0.348 | 0.001 | 9.92 |
| Unemployment rate | **0.536** | 0.001 | 14.70 |

All three variables show statistically significant positive spatial autocorrelation — neighboring regions tend to have similar values.

### 2. Spatial clusters of migration

- **High-High clusters** — Netherlands, Norway, Iceland, Sweden, Austria (attractive, prosperous regions surrounded by similar regions).
- **Low-Low clusters** — Bulgaria, North Macedonia, Greece, Western Romania (low-migration regions clustered together).
- **Outliers** — Bolzano (Low-High), South-East Romania and Cyprus (High-Low).

### 3. Model comparison

| Model | R² | AIC | Likelihood Ratio Test |
|---|---|---|---|
| OLS (log_PIB) | 0.215 | 2199.2 | — |
| **Spatial Lag (log_PIB)** | 0.374 | 2165.7 | 35.98 |
| **Spatial Error (log_PIB)** | **0.375** | **2164.7** | 34.93 |
| OLS (log_Salary) | 0.210 | 2201.4 | — |
| Spatial Lag (log_Salary) | 0.373 | 2166.1 | 34.68 |
| Spatial Error (log_Salary) | 0.374 | 2165.7 | 32.15 |

**Spatial Error Model** with log-transformed GDP shows the best overall fit. Spatial coefficients (ρ ≈ 0.48, λ ≈ 0.55) are positive and highly significant.

### 4. Significant predictors

- ✅ **GDP per capita** — positive effect (higher GDP → more immigration)
- ✅ **Average salary** — positive effect
- ✅ **Unemployment rate** — negative effect (higher unemployment → less immigration)
- ❌ Education, population density, poverty risk, crime rate, hospital beds, urbanization — not statistically significant

---

## Conclusions

1. **Migration in Europe is economically driven.** GDP, wages, and unemployment are the dominant push-pull factors. Social and infrastructure variables play a secondary role.
2. **Spatial spillovers matter.** Regions do not attract migrants in isolation — migration patterns spill over across borders. Ignoring spatial dependence produces biased estimates.
3. **Policy implication:** Migration policy should be **regional**, not just national. Improving economic conditions and wage competitiveness in lagging regions can reduce outward migration and strengthen neighboring areas.

---

## Tech Stack

- **Languages:** R, Python
- **Spatial analysis:** GeoDa, `spatialreg`, `spdep` (R)
- **Data manipulation:** `tidyverse`, `dplyr`, pandas
- **Visualization:** GeoDa, ggplot2, matplotlib, seaborn
- **Environment:** RStudio, Jupyter Notebook

---

## Repository Contents
