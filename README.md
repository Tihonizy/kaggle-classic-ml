# Kaggle Classic ML

Solutions to Kaggle competitions on tabular data with classical machine learning: feature
engineering, gradient boosting, tree models and hyperparameter search. Each competition has its
own folder, and notebooks are numbered in the order they were written.

[Русская версия](README.ru.md) · Kaggle profile: [tihon2010](https://www.kaggle.com/tihon2010)

## Projects

| Project | Task | Metric | Approach | Local result |
|---|---|---|---|---|
| [Titanic](titanic) | Predict passenger survival | Accuracy | Title and deck features, IQR outlier filtering, one-hot encoding, decision tree tuned with Hyperopt, 10-fold CV | 0.827 best CV accuracy during tuning |
| [House Prices](house-prices-advanced-regression-techniques) | Predict sale price of a house from 79 features | RMSE of log price | Missing values imputed with KNN, engineered area and age features, log-transformed target, CatBoost with early stopping, SHAP feature importance | 0.108 RMSE on the hold-out split |
| [Hull Tactical Market Prediction](hull-tactical-market-prediction) | Predict next-day S&P 500 excess returns and size a position | Volatility-adjusted Sharpe ratio | Leak-free feature selection, scaled features, CatBoost regressor, served through the Kaggle evaluation API | 0.648 on the validation split |

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
Hull Tactical is a code competition and runs on Kaggle, reading from `/kaggle/input`.

## License

[MIT](LICENSE)
