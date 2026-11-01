# Rainfall Prediction System

An end-to-end machine-learning project that looks at daily weather measurements and predicts whether it will rain. The goal is to support farmers and water-management agencies with earlier, data-driven planning.

The notebook is fully executed: every cell runs from raw CSV to trained models, with outputs and charts saved in the file.

## Dataset

`Rainfall.csv` contains **366 daily records** with 12 columns:

| Column | Meaning |
|---|---|
| `day` | Day index |
| `pressure` | Atmospheric pressure (hPa) |
| `maxtemp`, `temparature`, `mintemp` | Temperatures (°C) |
| `dewpoint` | Dew point (°C) |
| `humidity` | Relative humidity (%) |
| `cloud` | Cloud cover (%) |
| `sunshine` | Sunshine hours |
| `winddirection`, `windspeed` | Wind direction (degrees) and speed (km/h) |
| `rainfall` | Target — `yes` or `no` |

## What the notebook does

1. Imports pandas, NumPy, seaborn and matplotlib.
2. Loads `Rainfall.csv` and inspects shape, dtypes and summary statistics.
3. Strips trailing spaces from the column headers.
4. Drops the single incomplete record and checks for duplicates and garbage values.
5. Plots histograms, box plots, a correlation heatmap and the class balance.
6. Measures IQR whiskers to see how far the wind-speed outliers sit from the normal range.
7. Encodes the target — `yes → 1`, `no → 0` — and drops the `day` column, which only records the day of the month and carries no weather signal.
8. Splits the data 80/20 with stratification.
9. Trains Logistic Regression, Decision Tree, Random Forest and Gradient Boosting.
10. Compares them with test accuracy, F1 and 5-fold cross-validation.
11. Reports a confusion matrix and classification report for the winner.
12. Ranks feature importance using the Random Forest.

## Results

| Model | Test accuracy | F1 score | 5-fold CV accuracy |
|---|---|---|---|
| **Logistic Regression** | **0.822** | **0.871** | 0.792 |
| Gradient Boosting | 0.822 | 0.869 | 0.742 |
| Random Forest | 0.795 | 0.851 | 0.773 |
| Decision Tree | 0.726 | 0.796 | 0.671 |

Best model — Logistic Regression, on 73 held-out days:

| Class | Precision | Recall | F1 | Support |
|---|---|---|---|---|
| No rain | 0.73 | 0.70 | 0.71 | 23 |
| Rain | 0.86 | 0.88 | 0.87 | 50 |
| **Accuracy** | | | **0.82** | 73 |

Cloud cover, humidity and sunshine are the most important features — physically what you would expect for a rain-prediction problem.

## Project structure

```
rainfall_prediction.ipynb   Jupyter notebook with all analysis
Rainfall.csv                Daily weather dataset
screenshots.docx            Screenshots of the notebook output
requirements.txt            Python dependencies
```

## Getting started

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook rainfall_prediction.ipynb
```

Run the cells from top to bottom. The notebook expects `Rainfall.csv` to sit next to it.

## Future work

- [ ] Collect several years of records so seasonal patterns can be learned rather than memorised.
- [ ] Engineer rolling features (rain yesterday, 3-day averages) that capture the persistence of weather.
- [ ] Validate with a time-based split instead of a random one — the honest way to test a forecasting model.
- [ ] Save the trained model and expose a small prediction script or API.

## Tech stack

Python 3 · pandas · NumPy · scikit-learn · seaborn · matplotlib · Jupyter

## License

Released under the [MIT License](LICENSE).

## Author

**Lareb Malik** — [github.com/LEO-512](https://github.com/LEO-512)
