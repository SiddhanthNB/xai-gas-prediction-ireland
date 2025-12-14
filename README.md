# Gas Demand Prediction (Ireland)

Daily gas demand forecast for Ireland with clear, human-readable explanations. The work ties together gas demand/supply, Meteostat weather (temperature, wind), seasons, and Irish public holidays to show when and why consumption shifts.

What’s inside:
- `data/`: raw demand (`NGSD02.csv`), supply (`NGSD01.csv`), derived `final_df.csv`, and map assets.
- `data_preparation.ipynb`: turns raw files into a clean daily panel, enriches with Meteostat temperature and wind, assigns seasons, tags Irish public holidays, and computes demand–supply gaps.
- `gas_demand_prediction_ireland_xai.ipynb`: adds behavioral and temporal signals (weekend flag, seasonal one-hots, lags, rolling means, cyclical day-of-year), trains baseline and advanced forecasters (Linear Regression, SARIMAX, Random Forest, tuned XGBoost), and explains the best model with SHAP, PDP, and DiCE so each driver’s impact is visible.

Key outcomes:
- XGBoost performs best on the time-based split.
- Demand rises on cold, calm weekdays with recent high usage; warmer or windier periods and weekends ease it down.
- Explanations and forecasts are shown side by side in the notebook outputs.

Run order: `data_preparation.ipynb` (build `data/final_df.csv`) → `gas_demand_prediction_ireland_xai.ipynb` (modeling and explainability).

Requirements: Python 3 with the packages listed in `requirements.txt` (needs internet to fetch Meteostat weather and Irish holidays).