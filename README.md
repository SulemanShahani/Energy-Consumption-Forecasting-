# Time Series Forecasting for Energy Consumption in PJME Region

## Project Overview
This project aims to develop a machine learning model to predict future energy consumption (in megawatts) for the PJME region using historical hourly energy consumption data. The forecasting model leverages various time-based features, Fourier series terms, and lagged variables to capture seasonality and long-term trends. The model is trained and evaluated using XGBoost, a powerful and flexible gradient boosting framework.

## Data Preprocessing
### Loading Data:
- The dataset contains hourly energy consumption data for the PJME region.
- The data is indexed by datetime to facilitate time series analysis.

### Train/Test Split:
- Training set: Data before January 1, 2015.
- Test set: Data from January 1, 2015, onwards.
- This split ensures that the model is evaluated on a separate period to test its predictive power on unseen data.

### Visualization:
- A plot is created to visualize the train/test split.
- This helps in understanding the distribution and patterns in the data over time.

## Feature Creation
### Time-Based Features:
- Features such as hour, day of the week, quarter, month, year, and day of the year are extracted from the datetime index.
- These features help the model understand the temporal patterns in the data.

### Fourier Terms:
- Fourier series terms are added to capture seasonality.
- These terms help in modeling periodic patterns in the data.

### Lagged Variables:
- Lagged variables (e.g., 1 year, 2 years, 3 years back) are created to capture long-term seasonality.
- These variables help the model understand historical patterns and their impact on future values.

## Model Training and Evaluation
### Scaling:
- Features are scaled using StandardScaler to normalize the data.
- Scaling ensures that all features contribute equally to the model's learning process.

### Time Series Cross-Validation:
- Time series cross-validation with forward chaining is employed to validate the model on sequential data.
- This method ensures that the model is validated on future data points without any data leakage from the future to the past.

### Model Training:
- An XGBoost regressor is trained using the created features.
- XGBoost is chosen for its robustness and ability to handle complex patterns in the data.

### Evaluation:
- The model's performance is evaluated using Root Mean Squared Error (RMSE).
- RMSE is a standard metric for regression tasks that penalizes large errors, providing a clear measure of the model's accuracy.

## Hyperparameter Tuning
### Grid Search:
- GridSearchCV is used to find the optimal hyperparameters for the XGBoost model.
- This process involves testing various combinations of hyperparameters to find the best configuration that minimizes the RMSE.

### Best Model:
- The best model is selected based on the grid search results.
- The optimal parameters ensure that the model achieves the best possible performance.

## Future Predictions
### Feature Creation for Future Dates:
- An empty dataframe for future dates is created, and the same features as the training set are generated.
- This allows the model to make predictions on future time points.

### Scaling and Prediction:
- Future features are scaled using the same scaler fitted on the training data.
- Predictions are made using the trained XGBoost model.

### Visualization:
- Future predictions are visualized to provide a clear understanding of the expected future energy consumption.
- This visualization helps in assessing the model's forecasting ability and identifying potential trends.

## Performance Metrics
- **Best Parameters Found:**
  - learning_rate: 0.01
  - max_depth: 7
  - n_estimators: 500
  - reg_alpha: 0.001
  - reg_lambda: 1.0

- **Lowest RMSE Found:** 3497.96
- **Best RMSE on Training Data:** 2452.82
- **Mean Absolute Error (MAE):** 1792.87
- **Mean Squared Log Error (MSLE):** 0.0050
- **R² Score (Coefficient of Determination):** 0.8560

## Summary
This project successfully demonstrates the application of machine learning techniques to forecast energy consumption in the PJME region. The model leverages time-based features, Fourier series terms, and lagged variables to capture complex patterns in the data. Using XGBoost with rigorous cross-validation and hyperparameter tuning, the model achieves excellent performance metrics, indicating its robustness and accuracy. Future predictions provide valuable insights into expected energy consumption trends, aiding in efficient energy management and planning.

<img width="653" alt="prediction on current data" src="https://github.com/SulemanShahani/Time-Series-Forecasting-for-Energy-Consumption-in-PJME-Region/assets/164818514/3e168516-513b-41a2-9f44-63beb0f87e1b">

<img width="650" alt="predictions on future year" src="https://github.com/SulemanShahani/Time-Series-Forecasting-for-Energy-Consumption-in-PJME-Region/assets/164818514/a2a8610a-b270-4c7d-a0c7-dbe80d5910fc">


