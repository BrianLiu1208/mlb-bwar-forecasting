# MLB Subsequent-Season bWAR Forecasting

An interpretable machine-learning framework for forecasting MLB players'
subsequent-season Baseball-Reference Wins Above Replacement (bWAR).

This repository contains the final implementation from an MSc Business
Analytics dissertation. It integrates Statcast event-level data with historical
bWAR outcomes, converts player performance into six monthly observations
(April–September), and compares models of different complexity under a
chronological out-of-time evaluation design.

## Project overview

- **Predictor seasons:** 2015–2023
- **Target seasons:** 2016–2024 bWAR
- **Final observations:** 9,610 player-seasons
- **Sequence length:** 6 monthly observations
- **Feature selection:** 26 candidate predictors → 20 retained predictors,
  selected using training-period data only
- **Training:** 2015–2020
- **Validation:** 2021–2022
- **Held-out test:** 2023 predictors → 2024 bWAR
- **Models:** Ridge Regression, Random Forest, LSTM, Temporal Fusion Transformer
- **Interpretability:** LSTM SHAP and TFT native variable-selection / temporal attention

## Final held-out test results

| Model | RMSE | MAE | R² |
|---|---:|---:|---:|
| Ridge Regression | **1.373442** | 0.992555 | **0.227437** |
| LSTM | 1.380756 | **0.988436** | 0.219187 |
| Temporal Fusion Transformer | 1.385182 | 0.996271 | 0.214173 |
| Random Forest | 1.402113 | 1.004001 | 0.194846 |

The results show that greater model complexity did not consistently improve
out-of-time predictive accuracy. Ridge Regression achieved the lowest RMSE
and highest R², while the LSTM achieved the lowest MAE.

## Repository structure

```text
.
├── README.md
├── .gitignore
├── notebooks/
│   └── 01_end_to_end_pipeline.ipynb
├── data/
│   └── README.md
├── results/
│   └── figures/
└── src/
```

## Data

Raw Statcast and Baseball-Reference data are not included because of file size.
See [`data/README.md`](data/README.md) for the expected local filenames and
directory layout.

## Reproducibility note

The notebook contains the final dissertation implementation only. Earlier
experimental cells, duplicate code, and diagnostic-only metric calculations have
been removed. Final cross-model metrics are calculated globally over the same
1,106 held-out test observations.

## Next steps

- Pin the exact package versions from the original dissertation environment.
- Add selected dissertation figures to `results/figures/`.
- Optionally refactor reusable preprocessing/model utilities into `src/`.
