 Results Summary

| Metric | Value |
|---|---|
| Raw trip records analyzed | ~3,000,000+ |
| Records after data cleaning | ~2,800,000+ |
| Weekday vs weekend fare difference | Statistically significant (t = -4.426, p = 0.00001) |
| Trip duration prediction — R² | 0.77 |
| Trip duration prediction — MAE | ~4.05 minutes |
| Top predictor of trip duration | Trip distance, followed by pickup hour |
| Model used | Random Forest Regressor (150 trees, max depth 12) |

 Challenges & Learnings
- **Data quality at scale:** With millions of raw records, even a small percentage of bad rows (negative fares, zero-second trips, GPS errors) translates into thousands of corrupted data points — reinforcing that rigorous cleaning isn't optional at this scale.
- **Choosing the right tool for the job:** Initially planned this with PySpark for distributed processing, but for a single-month dataset, pandas with sampling proved simpler, faster to debug, and just as effective — a reminder that "big data" tools aren't always the right fit for every big dataset.
- **Correlation vs. causation:** The initial weekday/weekend fare comparison looked meaningful on its own, but running a formal t-test was necessary to confirm the difference wasn't just random variation — a key statistical discipline for any data-driven business claim.
- **Feature engineering value:** Simple derived features (pickup hour, weekend flag, average speed) added far more predictive power than expected, reinforcing that thoughtful feature engineering often matters more than model complexity.

Future Improvements
- Incorporate weather data (rain, snow, temperature) as an additional predictor of trip duration and demand
- Extend the analysis across multiple months to capture seasonal trends rather than a single snapshot
- Add a live/interactive dashboard (e.g., with Plotly Dash or Streamlit) for exploring demand patterns dynamically
- Experiment with gradient boosting models (XGBoost/LightGBM) to compare performance against the Random Forest baseline
- Incorporate real-time traffic data to improve trip duration prediction accuracy further
