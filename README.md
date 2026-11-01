# Rainfall Prediction System

An exploratory machine-learning project that looks at daily weather measurements and tries to predict whether it will rain. The goal is to support farmers and water-management agencies with earlier, data-driven planning.

> **Status: exploratory.** The notebook covers data inspection, cleaning, outlier handling, encoding and the train/test split. Model training and evaluation are not implemented yet — see [Roadmap](#roadmap).

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
3. Checks for missing values and duplicate rows.
4. Explores garbage values in the categorical columns.
5. Plots histograms, box plots and scatter plots for every numeric feature.
6. Computes IQR whiskers for outlier treatment.
7. Strips whitespace from column names.
8. One-hot encodes the `temparature` and `pressure` columns.
9. Splits the data 80/20 into training and test sets with a fixed random seed.

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

## Roadmap

- [ ] Fix the target encoding — `rainfall` is converted to numbers and then mapped as `yes`/`no` in different cells; settle on one encoding.
- [ ] Train a baseline Logistic Regression classifier.
- [ ] Compare Decision Tree, Random Forest and Gradient Boosting.
- [ ] Report accuracy, precision, recall, F1 and a confusion matrix.
- [ ] Add a small script that loads a saved model and predicts from new weather readings.

## Tech stack

Python 3 · pandas · NumPy · scikit-learn · seaborn · matplotlib · Jupyter

## License

Released under the [MIT License](LICENSE).

## Author

**Lareb Malik** — [github.com/LEO-512](https://github.com/LEO-512)
