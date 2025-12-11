# 🚀 Cryptocurrency Price Forecasting with Machine Learning

A comprehensive Streamlit application that compares three powerful time series forecasting models (ARIMA, Prophet, and LSTM) for cryptocurrency price prediction.

## 📋 Overview

This application provides an interactive interface to train, evaluate, and compare multiple machine learning models for cryptocurrency price forecasting. It includes automated data preprocessing, model training with visual feedback, performance metrics, and future price predictions.

## ✨ Features

- **Multiple Model Support**: Compare ARIMA, Prophet, and LSTM models side-by-side
- **Interactive Configuration**: Adjustable test/validation splits, lookback periods, and forecast horizons
- **Visual Analytics**: Comprehensive charts for historical data, predictions, and forecasts
- **Performance Metrics**: MAE and RMSE calculations for model comparison
- **Future Predictions**: Generate multi-day price forecasts with trained models
- **Reproducible Results**: Fixed random seeds for consistent model training

## 🛠️ Technologies Used

- **Frontend**: Streamlit
- **ML/DL Framework**: TensorFlow/Keras
- **Time Series Models**: 
  - ARIMA (via pmdarima)
  - Prophet (Facebook)
  - LSTM (Deep Learning)
- **Data Processing**: pandas, numpy, scikit-learn
- **Visualization**: matplotlib

## 📦 Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/crypto-price-forecasting.git
cd crypto-price-forecasting
```

2. Create a virtual environment (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install required packages:
```bash
pip install -r requirements.txt
```

### Requirements

Create a `requirements.txt` file with the following dependencies:

```
streamlit>=1.28.0
numpy>=1.24.0
pandas>=2.0.0
matplotlib>=3.7.0
tensorflow>=2.13.0
scikit-learn>=1.3.0
joblib>=1.3.0
pmdarima>=2.0.0
statsmodels>=0.14.0
prophet>=1.1.0
```

## 🚀 Usage

1. Start the Streamlit application:
```bash
streamlit run cryptoapp.py
```

2. Upload your CSV file with the required format:
   - `snapped_at`: Datetime column (e.g., '2024-01-01 00:00:00')
   - `price`: Numeric price values

3. Configure parameters in the sidebar:
   - **Test Size**: Percentage of data for testing (5-20%)
   - **Validation Size**: Percentage of data for validation (5-20%)
   - **LSTM Lookback Period**: Number of past days to consider (30-90)
   - **Future Forecast Days**: Number of days to predict ahead (30-90)

4. Click "🚀 Train All Models" to start the training process

5. Review the results:
   - Model performance comparison
   - Historical vs predicted prices
   - Future price forecasts

## 📊 Data Format

Your CSV file should have the following structure:

```csv
snapped_at,price
2024-01-01 00:00:00,45000.50
2024-01-02 00:00:00,45200.75
2024-01-03 00:00:00,44800.25
...
```

## 🤖 Models Explained

### 1. ARIMA (AutoRegressive Integrated Moving Average)
- Traditional statistical model for time series forecasting
- Automatically selects optimal parameters using `auto_arima`
- Performs stationarity testing with Augmented Dickey-Fuller test
- Best for: Linear trends and stable patterns

### 2. Prophet
- Developed by Facebook's Core Data Science team
- Handles seasonality, holidays, and missing data automatically
- Robust to outliers and trend changes
- Best for: Data with strong seasonal patterns

### 3. LSTM (Long Short-Term Memory)
- Deep learning model specialized for sequence prediction
- Captures complex non-linear patterns
- Uses 60-day lookback window (configurable)
- Architecture: 2 LSTM layers with dropout for regularization
- Best for: Complex patterns and long-term dependencies

## 📈 Performance Metrics

The application evaluates models using:
- **MAE (Mean Absolute Error)**: Average absolute difference between predictions and actual values
- **RMSE (Root Mean Squared Error)**: Square root of average squared differences (penalizes larger errors)

## 🎯 Model Training Process

1. **Data Preprocessing**: Automatic resampling to daily frequency and forward filling
2. **Train/Val/Test Split**: Configurable split ratios with chronological ordering
3. **Model Training**: 
   - ARIMA: Automated parameter selection
   - Prophet: Daily seasonality detection
   - LSTM: Early stopping and model checkpointing
4. **Validation**: Performance evaluation on validation set
5. **Final Training**: LSTM retrained on train+validation data
6. **Testing**: Final evaluation on held-out test set
7. **Forecasting**: Multi-step ahead predictions for future dates

## 🔧 Configuration Options

| Parameter | Range | Default | Description |
|-----------|-------|---------|-------------|
| Test Size | 5-20% | 10% | Portion of data for final testing |
| Validation Size | 5-20% | 10% | Portion of data for model validation |
| LSTM Lookback | 30-90 days | 60 days | Historical window for LSTM |
| Future Forecast | 30-90 days | 60 days | Number of days to predict |

## 📝 Notes

- The application uses fixed random seeds (SEED=42) for reproducibility
- LSTM training may take several minutes depending on data size
- Models are automatically retrained on combined train+validation data for final predictions
- All date/time data is converted to timezone-naive format for consistency

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- ARIMA implementation using pmdarima
- Prophet by Facebook's Core Data Science team
- TensorFlow/Keras for deep learning capabilities
- Streamlit for the interactive web interface

## 📧 Contact

For questions or feedback, please open an issue on GitHub.
