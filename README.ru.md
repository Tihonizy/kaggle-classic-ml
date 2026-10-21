# Kaggle Classic ML

Решения соревнований Kaggle на табличных данных классическими методами машинного обучения:
генерация признаков, градиентный бустинг, деревья решений, подбор гиперпараметров. У каждого
соревнования своя папка, ноутбуки пронумерованы в порядке написания.

[English version](README.md) · Профиль на Kaggle: [tihon2010](https://www.kaggle.com/tihon2010)

## Проекты

| Проект | Задача | Метрика | Подход | Локальный результат |
|---|---|---|---|---|
| [Titanic](titanic) | Предсказать, выжил ли пассажир | Accuracy | Признаки из титула и палубы, фильтрация выбросов по IQR, one-hot кодирование, дерево решений с подбором параметров через Hyperopt, 10-fold CV | 0.827, лучшая accuracy на CV при подборе |
| [House Prices](house-prices-advanced-regression-techniques) | Предсказать цену дома по 79 признакам | RMSE логарифма цены | Заполнение пропусков через KNN, признаки площади и возраста, логарифм целевой переменной, CatBoost с early stopping, важность признаков через SHAP | 0.108 RMSE на отложенной выборке |
| [Hull Tactical Market Prediction](hull-tactical-market-prediction) | Предсказать дневную избыточную доходность S&P 500 и размер позиции | Коэффициент Шарпа с поправкой на волатильность | Отбор признаков без утечек, масштабирование, CatBoost, предсказания через Kaggle evaluation API | 0.648 на валидации |

## Структура

```
.
├── titanic/
├── house-prices-advanced-regression-techniques/
├── hull-tactical-market-prediction/
├── requirements.txt
└── LICENSE
```

Папки названы по адресу соревнования на Kaggle, ноутбуки по схеме `NN_short_description.ipynb`.
Данные лежат в `<проект>/data/` и в git не попадают.

## Запуск

```bash
pip install -r requirements.txt
kaggle competitions download -c titanic -p titanic/data
```

Titanic и House Prices читают `data/train.csv` и `data/test.csv` рядом с ноутбуком.
Hull Tactical это code competition, он запускается в Kaggle и читает данные из `/kaggle/input`.

## Лицензия

[MIT](LICENSE)
