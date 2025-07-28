### Project Title: Exploratory Data Analysis and Advanced Modeling for Rent Prediction  
**Author:** Sweta Kumari Prasad  

---

#### Executive Summary  
This project predicts monthly rental prices across U.S. states and cities by analysing housing, economic and seasonal indicators.  
* Thorough **EDA** uncovered geographic rent hot-spots (e.g., NY & CA) and strong correlations with list price, construction cost and seasonal terms.  
* Feature engineering produced property-mix ratios, tier spreads, log‐scaled price fields and calendar parts.  
* A baseline **Linear Regression (OLS)** reached **RMSE ≈ \$100** (≈ 6 % of mean rent \$1 670) with **R² ≈ 0.94**, explaining the vast majority of variance.  
* A robust modeling pipeline, with the Stacked Ensemble achieving the best predictive performance (Test RMSE ≈ $418.72, Test R² ≈ 0.967).
* A SARIMAX-based time-series forecasting approach providing future rent trends.
* **Zillow Home Value Index (ZHVI):** A measure of the typical home value and market changes across a given region and housing type. It reflects the typical value for homes in the 35th to 65th percentile range. Available as a smoothed, seasonally adjusted measure and as a raw measure.
* **Zillow Observed Rent Index (ZORI):** A smoothed measure of the typical observed market rate rent across a given region. ZORI is a repeat-rent index that is weighted to the rental housing stock to ensure representativeness across the entire market, not just those homes currently listed for-rent. The index is dollar-denominated by computing the mean of listed rents that fall into the 35th to 65th percentile range for all homes and apartments in a given region, which is weighted to reflect the rental housing stock.
* **Zillow Observed Renter Demand Index (ZORDI):** A measure of the typical observed rental market engagement across a region. ZORDI tracks engagement on Zillow’s rental listings to proxy changes in rental demand. The metric is smoothed to remove volatility.



---

#### Rationale – Why This Matters  
* **Renters** can anticipate cost-of-living shifts and negotiate smarter.  
* **Policymakers** gain quantitative insight to tackle affordability and zoning.  
* **Investors / Developers** can spot high-growth, high-spread markets to optimise capital.  
With rising housing costs and urban migration, a data-driven rent forecast supports better planning and decision-making at every level.

---

#### Research Question  
> *What factors drive regional rent levels, and how accurately can we forecast future rents using historical housing and economic data?*  

Objectives  
1. Pinpoint the most influential features (housing tiers, list prices, market indicators).  
2. Build a modelling for rent prediction.  
3. Interactive Streamlit dashboard visualizing rent trends and forecasts.

---

#### Data Sources  

| Source | Key Fields |
|--------|-----------|
| **Zillow Housing Data** | `AllHomesRent`, tiered rents, `MedianListPrice`, ZORI, ZORDI |
| **Construction & Sales** | New-construction sale price, price-per-sqft |
| **Market Indicators** | `%SoldBelowList`, seasonal flags |
| **Geography** | `RegionName`, `StateName` |

Data is cleaned, outliers handled, and transformed appropriately.

---

#### Methodology  

| Step | Notebook | Key Actions |
|------|----------|-------------|
| **1. Data Assembly** | `RentPredictionMergeData.ipynb` | Merge all raw Zillow & auxiliary tables → master dataframe |
| **2. Missing-Value Handling** | `RentPredictionHandleMissingValues.ipynb` | KNN imputation, drop high-NA columns, one-hot low-cardinality cats |
| **3. EDA & Feature Engineering** | `RentPredictionVisualization.ipynb` | Skew checks, correlation heatmap, ratio & log features, seasonality parts |
| **4. Baseline Modelling** | `RentPredictionBaselineModel.ipynb` | OLS pipeline (one-hot + scaler), Ridge grid search, residual & importance plots |
| **5. Advanced Modeling** | `RentPredictionModelling.ipynb` | Model training and comparison (Random Forest, KNN, Stacked Ensemble), residual diagnostics |
| **6. Future Trend Forecasting** | `RentPredictionFutureTrend_trail.ipynb` | SARIMAX-based time-series forecasts for top cities/states |

Core pipeline: **merge → clean/impute → outlier handling → feature engineering → baseline and advanced modeling → forecast future trends.**.

---

#### Results  

* **Baseline OLS:** RMSE ≈ \$99.6, R² ≈ 0.94  
* **Ridge:** no improvement (α ≈ 0 best).  
* **Top drivers:** `MedianListPrice`, `TopTier/BottomTier` ratio, `Condo/SF` ratio, log-tier rents; positive state intercepts for CA, NY, MA, WA.  
* **Residuals:** no global bias, but heteroscedastic and mildly non-linear fan-shape.  
* **Outlier winsorising** lowered RMSE by ≈ \$10 and halved CV variance.
* **Stacked Ensemble:** Best predictive performance with Test RMSE ≈ $418.72, Test R² ≈ 0.967.
* **Top predictive features:** MedianListPrice, bedroom counts (3BHK, 4BHK), SingleFamilyRent, TopTier rent.
* **Geographic Insights:** Highest rents in NY, CA, MA, and WA.
* **Seasonality:** Clear seasonal patterns identified through SARIMAX modeling.

---

#### Next Steps  

| Technique | Purpose |
|-----------|---------|
| **Additional Economic Indicators** | Enhance model performance |
| **Extended Forecasts** | Broaden geographic coverage and forecast periods |
| **Explainable AI (SHAP)** | Deepen model interpretability |

---

#### Outline of Project  

- [RentPredictionMergeData.ipynb](RentPredictionMergeData.ipynb)
- [RentPredictionHandleMissingValues.ipynb](RentPredictionHandleMissingValues.ipynb)
- [RentPredictionVisualization.ipynb](RentPredictionVisualization.ipynb)  
- [RentPredictionBaselineModel.ipynb](RentPredictionBaselineModel.ipynb)
- [RentPredictionModelling.ipynb](link_to_notebook5)
- [RentPredictionFutureTrend.ipynb](link_to_notebook6)

---
##### Contact and Further Information  

| Field | Details |
|-------|---------|
| **Name** | Sweta Kumari Prasad |
| **Email** | <swetakumari.prasad@gmail.com> |
| **GitHub** | [github.com/SwetaKumariPrasad](https://github.com/SwetaKumariPrasad) |
| **LinkedIn** | [linkedin.com/in/swetakumariprasad](https://www.linkedin.com/in/swetakumariprasad/) |
| **Project Repository** | [github.com/SwetaKumariPrasad/Rent-Prediction/tree/main](https://github.com/SwetaKumariPrasad/Rent-Prediction/tree/main) |
| **Primary Data Source** | [Zillow Research Data](https://www.zillow.com/research/data/) |

