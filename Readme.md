# Port Authority Traffic Analytics

This project analyzes traffic patterns across Port Authority tunnels and bridges using machine learning models built with **H2O AutoML and Python**. The objective is to identify key drivers of roadway demand and develop predictive models to support infrastructure planning, congestion management, and revenue forecasting.

---

## Project Overview

Transportation agencies rely on accurate traffic forecasting to plan infrastructure investments and manage congestion. In this project, historical traffic, mobility speed data, and regional transit demand were integrated to build machine learning models capable of predicting monthly traffic volumes.

The analysis combines **data engineering, exploratory analysis, AutoML modeling, and Python machine learning replication** to produce interpretable and reliable predictive insights.

---

## Dataset

The dataset was created by integrating multiple Port Authority data sources including:

- Traffic volume records from tunnels and bridges
- Mobility speed metrics
- Regional transit demand (PABT bus and passenger volumes)

### Key Variables

- **TOTAL_TRAFFIC** – Monthly vehicle volume
- **YEAR, MONTH** – Seasonal patterns
- **Facility** – Tunnel or bridge location
- **Direction** – Traffic direction
- **Avg_Speed, Freeflow, Delta** – Mobility speed indicators
- **PABT_Bus_Volume** – Bus activity
- **PABT_Passenger_Volume** – Transit passenger demand

The final modeling dataset contains **146 monthly observations**.

---

## Project Workflow

The project follows a structured analytics workflow:

1. **Data Cleaning & Integration**
   - Combined multiple transportation datasets
   - Handled missing values and inconsistencies
   - Created a unified modeling dataset

2. **Exploratory Data Analysis**
   - Descriptive statistics
   - Traffic trend visualization
   - Correlation analysis

3. **Feature Engineering**
   - Seasonal variables
   - Regional mobility indicators
   - Facility-level characteristics

4. **Model Development**
   - H2O AutoML model selection
   - Gradient Boosting Machine regression
   - Python replication using scikit-learn

5. **Business Interpretation**
   - Identification of demand drivers
   - Infrastructure planning insights

---

## Model 1 – Traffic Volume Prediction (Regression)

The primary model predicts **monthly TOTAL_TRAFFIC**.

### Algorithm
**Gradient Boosting Machine (GBM)** selected via H2O AutoML.

### Leakage Prevention

The following variables were excluded from the final model because they are structural components of total traffic:

- TOTAL_EZPASS
- TOTAL_CASH
- TOTAL_VIOLATIONS

Removing these variables ensures the model predicts **true demand drivers rather than accounting relationships**.

### Model Performance

| Metric | Value |
|------|------|
| RMSE | 18,111 |
| MAE | 11,408 |
| R² | 0.999 |

Relative error is approximately **0.18% of average monthly traffic**.

---

## Key Insights

The model reveals several important traffic drivers:

1. **Seasonality (MONTH)**  
   Traffic patterns follow strong cyclical seasonal trends.

2. **Regional Transit Demand**  
   PABT passenger and bus volumes strongly correlate with roadway traffic.

3. **Long-Term Growth (YEAR)**  
   Structural changes in demand appear over time.

4. **Mobility Speeds**  
   Speed variables reflect congestion but are weaker predictors of demand.

---

## Python Model Replication

The AutoML model was replicated in Python using:

- `scikit-learn`
- `GradientBoostingRegressor`
- 5-fold cross-validation

Python results:

| Metric | Value |
|------|------|
| RMSE | 315,453 |
| Relative Error | ~3.15% |

Differences between H2O and Python performance arise from implementation differences and categorical encoding methods.

---

## Tools & Technologies

- Python
- Pandas
- scikit-learn
- H2O AutoML
- Jupyter Notebook
- Data visualization libraries

---

## Future Work

The next steps of the project include:

- **Model 2 – Classification**
  - Predict high-violation or congestion periods.

- **Model 3 – Forecasting**
  - Long-term traffic demand projections.

---

## Author

Yusuf Rahat  
Master’s in Business Analytics – University of New Haven
