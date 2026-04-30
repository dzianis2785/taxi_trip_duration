# NYC Taxi Trip Duration

This project predicts the duration of taxi rides in New York City using supervised regression models.

The work is implemented in the Jupyter notebook [`NYC_Taxi_Project.ipynb`](NYC_Taxi_Project.ipynb) and expects the dataset at [`data/data.csv`](data/data.csv).

## Project Goal

Build and compare several regression models for estimating `trip_duration` from trip metadata, geospatial information, and engineered features.

## Dataset

The notebook uses one prepared dataset with 1,458,644 rows and the following source columns:

`id`, `vendor_id`, `pickup_datetime`, `dropoff_datetime`, `passenger_count`, `pickup_longitude`, `pickup_latitude`, `dropoff_longitude`, `dropoff_latitude`, `store_and_fwd_flag`, `trip_duration`

The notebook expands these raw fields with additional features such as:

- datetime-based features
- holiday and day-of-week indicators
- geospatial distance features
- weather-related features
- cluster-based location features

Note: the raw CSV is kept outside version control because of its size. Place it at `data/data.csv` before running the notebook.

## Workflow

1. Load and inspect the raw trip data.
2. Perform exploratory data analysis.
3. Engineer predictive features.
4. Encode categorical variables and scale numeric features where needed.
5. Train and compare several regression models.
6. Evaluate models with RMSLE on a validation split.
7. Use the best model for the final prediction step.

## Models Evaluated

The notebook compares:

- Linear Regression
- Polynomial Regression
- Ridge Regression
- Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor

## Results

According to the notebook, the best validation performance was achieved by `GradientBoostingRegressor`.

- Best validation RMSLE: about `0.39`
- Strong baseline models:
  - Linear Regression: about `0.54`
  - Ridge Regression: about `0.48`
  - Random Forest Regressor: about `0.41`

Feature importance is also analyzed for the final tree-based model.

## Repository Structure

- [`NYC_Taxi_Project.ipynb`](NYC_Taxi_Project.ipynb) - main analysis and modeling notebook
- [`data/data.csv`](data/data.csv) - input dataset
- [`requirements.txt`](requirements.txt) - Python dependencies used in the notebook

## Setup

Create a virtual environment and install the dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Make sure `data/data.csv` is available locally before launching the notebook.

## Run

Launch Jupyter and open the notebook:

```bash
jupyter notebook
```

Then run the cells in `NYC_Taxi_Project.ipynb` from top to bottom.

## Notes

- The project is notebook-driven rather than packaged as a standalone Python module.
- Dependencies in `requirements.txt` are pinned to keep the notebook environment reproducible.
