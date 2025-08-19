# Walmart Sales Forecasting Project 📊

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](the-walmart-sales-forecast.ipynb)

## Overview
This repository contains a Jupyter notebook demonstrating an end-to-end machine learning pipeline for forecasting weekly sales at Walmart stores. The project leverages historical sales data, store information, and economic features to build and evaluate predictive models. Key components include:

- **Data Loading & Quality Assessment**: Handling multiple datasets with checks for integrity.
- **Exploratory Data Analysis (EDA)**: Visualizations of sales patterns, seasonal trends, and relationships.
- **Data Preprocessing**: Cleaning, feature engineering (e.g., date decomposition, handling missing values), and scaling.
- **Model Training & Evaluation**: Testing algorithms like Linear Regression, Random Forest, Gradient Boosting, XGBoost, and LightGBM. Metrics include MAE, RMSE, and R².
- **Feature Importance**: Analysis of key drivers like store size, department, holidays, and economic indicators (CPI, unemployment).
- **Visualizations**: Plots for predictions vs. actuals, residuals, and error distributions.

The best-performing model (LightGBM) achieves strong predictive accuracy, making it suitable for inventory planning and demand forecasting.

## Dataset
The dataset is sourced from Kaggle's [Walmart Recruiting - Store Sales Forecasting](https://www.kaggle.com/competitions/walmart-recruiting-store-sales-forecasting/data) competition. It includes:
- **stores.csv**: Store type and size (45 stores).
- **train.csv**: Historical weekly sales (2010-2012) for 99 departments across stores.
- **features.csv**: Economic indicators (e.g., CPI, unemployment, fuel prices) and holiday flags.
- **test.csv**: Data for predictions.

**Note**: Data files are not included in this repo due to size and licensing. Download them from Kaggle and place in a `data/raw/` directory.

- Training period: Feb 2010 - Oct 2012
- Features: Temporal (date, week, month), store-specific, economic, and holiday markdowns.
- Target: Weekly sales (numeric).

## Installation
1. Clone the repository:
   ```
   git clone https://github.com/your-username/walmart-sales-forecast.git
   cd walmart-sales-forecast
   ```

2. Create a virtual environment (recommended):
   ```
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

4. Download the dataset from Kaggle and extract to `data/raw/`.
   - Ensure files are named: `stores.csv`, `train.csv`, `features.csv`, `test.csv`.

5. (Optional) For Jupyter:
   ```
   pip install jupyter
   jupyter notebook
   ```

## Usage
1. Open the notebook:
   ```
   jupyter notebook the-walmart-sales-forecast.ipynb
   ```

2. Run cells sequentially:
   - Sections are modular (e.g., data loading, EDA, modeling).
   - Adjust paths if not using the default `data/raw/` directory.
   - For production predictions, use the trained LightGBM model on `test.csv`.

3. Key Outputs:
   - Processed data saved to `data/processed/`.
   - Models saved to `models/`.
   - Visualizations: Sales trends, feature importance, prediction vs. actual plots.

Example prediction snippet (from notebook):
```python
# After training
predictions = best_model.predict(X_test)
```

## Results
- **Best Model**: LightGBM (R² ~0.95 on test set, depending on data split).
- **Metrics** (example from notebook run):
  - MAE: ~$1,500 (varies by department/store).
  - RMSE: ~$2,200.
  - Key Features: Department, Store Size, Week of Year, Holidays.
- Insights: Sales peak during holidays; economic factors like CPI negatively correlate with sales.

See the notebook's "Model Evaluation" and "Conclusions" sections for detailed tables and plots.

## Conclusions & Recommendations
- **Strengths**: Handles seasonality and external factors well; ensemble models outperform linear ones.
- **Limitations**: Assumes stationary data; may need retraining for new economic shifts.
- **Recommendations**:
  - Deploy LightGBM for real-time forecasting.
  - Incorporate more features (e.g., weather data) for better accuracy.
  - Monitor for concept drift in production.

## Contributing
Pull requests welcome! For major changes, open an issue first.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Dataset: Walmart via Kaggle.
- Libraries: scikit-learn, LightGBM, XGBoost, Pandas, etc.