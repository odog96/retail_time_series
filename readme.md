# Retail Time Series Forecasting

This repository implements various techniques for forecasting retail sales data, with a focus on the N-BEATS (Neural Basis Expansion Analysis for interpretable Time Series forecasting) model.

## Dataset

The project uses the [Walmart Store Sales Forecasting dataset](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting), which includes:

- Historical sales data for 45 Walmart stores
- Weekly sales from 2010-02-05 to 2012-11-01
- Store and department level granularity
- Additional features like markdown events, CPI, unemployment rate etc.

## Model Architecture

The implementation uses the N-BEATS architecture with the following configuration:

- Input sequence length: 80 time steps
- Forecast horizon: 40 time steps 
- Hidden layer size: 512 neurons
- Stack layers: 30
- Epochs: 5000
- Batch size: 1024

## Data Preprocessing

The raw data undergoes several preprocessing steps:
1. Serialization of store-department combinations
2. Filtering out series with insufficient data:
   - Removed series with less than 52 weeks of historical data
   - Removed series missing data in last 6 months
3. Missing value imputation using forward fill
4. Normalization of input features

## Model Performance

The model is evaluated using several metrics:
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE) 
- Mean Absolute Percentage Error (MAPE)

### Training Configuration
- Window size: 80 weeks input
- Prediction horizon: 40 weeks
- Validation split: Last 40 weeks of data
- Early stopping with patience of 10 epochs

### Performance Metrics
[Insert key performance metrics here when available]

## Project Structure

```
├── NBEATS_Walmart_Retail_Data.ipynb   # Main notebook with model implementation
├── readme.md                          # Project documentation
```

## Usage

The implementation is available in the Jupyter notebook. To use:

1. Download the Walmart dataset from Kaggle
2. Run the data preprocessing steps
3. Train the N-BEATS model
4. Generate forecasts

## Next Steps

Planned enhancements:
- Add Facebook Prophet based forecasts
- Incorporate additional features (markdowns, store attributes)
- Experiment with hybrid models
- Add cross-validation
- Ensemble multiple models

## References

- [N-BEATS Original Paper](https://arxiv.org/abs/1905.10437)
- [Walmart Store Sales Forecasting Competition](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting)