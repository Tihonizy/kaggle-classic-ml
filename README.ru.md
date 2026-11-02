# Kaggle Classic ML

Решения соревнований Kaggle на табличных данных классическими методами машинного обучения:
генерация признаков, градиентный бустинг, деревья решений, подбор гиперпараметров. У каждого
соревнования своя папка, ноутбуки пронумерованы в порядке написания.

[English version](README.md) · Профиль на Kaggle: [tihon2010](https://www.kaggle.com/tihon2010)

## Проекты

| Проект | Задача | Метрика | Подход | Локальный результат |
|---|---|---|---|---|
| [Titanic](titanic) | Предсказать, выжил ли пассажир | Accuracy | Признаки из титула и палубы, фильтрация выбросов по IQR, one-hot кодировщик обучен только на train, дерево решений с подбором параметров через Hyperopt на 5-fold CV | 0.809 ± 0.041 accuracy, стратифицированная 10-fold CV |
| [House Prices](house-prices-advanced-regression-techniques) | Предсказать цену дома по 79 признакам | RMSE логарифма цены | Заполнение пропусков через KNN, признаки площади и возраста, логарифм целевой переменной, CatBoost с early stopping, важность признаков через SHAP | 0.108 RMSE на отложенной выборке |
| [Hull Tactical Market Prediction](hull-tactical-market-prediction) | Предсказать дневную избыточную доходность S&P 500 и размер позиции | Коэффициент Шарпа с поправкой на волатильность | Разбиение по времени (последние 20% дней на валидацию), заполнение пропусков и масштабирование обучены только на прошлых днях, CatBoost, предсказания через Kaggle evaluation API | 0.563 на последних 20% дней, ниже стратегии buy and hold (0.624) |

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

Локально каждый ноутбук читает файлы соревнования из `data/` рядом с собой и туда же пишет `submission.csv`
(Hull Tactical: `kaggle competitions download -c hull-tactical-market-prediction -p hull-tactical-market-prediction/data`).

Каждый ноутбук начинается с ячейки Environment с одним флагом `ON_KAGGLE = False`. Перед запуском в Kaggle его меняют
на `True`: данные читаются из `/kaggle/input`, сабмит пишется в `/kaggle/working`. Hull Tactical это code competition,
его сабмит делается только из ноутбука в Kaggle.

## Лицензия

[MIT](LICENSE)
