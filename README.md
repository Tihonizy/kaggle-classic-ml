# Kaggle Classic ML

Solutions to Kaggle competitions on tabular data with classical machine learning: feature
engineering, gradient boosting, tree models and hyperparameter search. Each competition has its
own folder, and notebooks are numbered in the order they were written.

[Русская версия](README.ru.md) · Kaggle profile: [tihon2010](https://www.kaggle.com/tihon2010)

## Projects

| Project | Task | Metric | Approach | Local result |
|---|---|---|---|---|
| [Titanic](titanic) | Predict passenger survival | Accuracy | Title and deck features, IQR outlier filtering, one-hot encoder fitted on the training set only, decision tree tuned with Hyperopt on 5-fold CV | 0.809 ± 0.041 accuracy, stratified 10-fold CV |
| [House Prices](house-prices-advanced-regression-techniques) | Predict sale price of a house from 79 features | RMSE of log price | Missing values imputed with KNN, engineered area and age features, log-transformed target, CatBoost with early stopping, SHAP feature importance | 0.108 RMSE on the hold-out split |
| [Hull Tactical Market Prediction](hull-tactical-market-prediction) | Predict next-day S&P 500 excess returns and size a position | Volatility-adjusted Sharpe ratio | Chronological split (last 20% of days for validation), imputation and scaling fitted on past days only, CatBoost regressor, served through the Kaggle evaluation API | 0.563 on the last 20% of days, below buy and hold (0.624) |

## Repository layout

```
.
├── titanic/
├── house-prices-advanced-regression-techniques/
├── hull-tactical-market-prediction/
├── requirements.txt
└── LICENSE
```

Folders are named after the Kaggle competition slug. Notebooks are named
`NN_short_description.ipynb`. Competition data goes to `<project>/data/` and is not tracked.

## Running the notebooks

```bash
pip install -r requirements.txt
kaggle competitions download -c titanic -p titanic/data
```

Titanic and House Prices read `data/train.csv` and `data/test.csv` relative to the notebook.
Hull Tactical is a code competition: on Kaggle it reads from `/kaggle/input`, locally from `data/`
(`kaggle competitions download -c hull-tactical-market-prediction -p hull-tactical-market-prediction/data`).

## License

[MIT](LICENSE)
