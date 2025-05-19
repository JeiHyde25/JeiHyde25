# Coffee Sales Forecasting App

## Overview
This project implements a sales forecasting system for coffee shops using linear regression and provides an interactive web interface using Streamlit. It processes historical sales data to predict daily revenue, helping coffee shop owners make informed business decisions.

**Live Demo:** [Coffee Sales Forecast App](https://coffee-forecast-app.onrender.com)

## Features
- Interactive web interface with Streamlit
- Real-time sales predictions for specific dates
- Future sales forecasting (up to 30 days)
- Historical sales data visualization
- Detailed performance metrics dashboard
- Interactive data tables and charts

## Technology Stack
- Python 3.x
- Streamlit
- pandas
- scikit-learn
- matplotlib
- kagglehub
- Docker

## Project Structure
```
.
├── notebook.py           # Main application file with Streamlit interface
├── data/                # Data directory for CSV files
│   ├── index_1.csv     # First part of the dataset
│   └── index_2.csv     # Second part of the dataset
├── model_metrics.txt    # Model performance metrics
├── requirements.txt     # Project dependencies
├── Dockerfile          # Docker configuration file
└── future_predictions.csv # Generated predictions
```

## Installation and Usage

### Option 1: Local Installation

1. Clone the repository:
```bash
git clone https://github.com/JeiHyde25/jeihyde-proj.git
cd coffee_sales_forecast
```

2. Create a virtual environment and activate it:
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Set up Kaggle credentials (if using Kaggle dataset):
```bash
mkdir -p ~/.kaggle
# Move your kaggle.json file to ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json
```

5. Run the Streamlit app:
```bash
streamlit run notebook.py
```

### Option 2: Using Docker

1. Clone the repository (if you haven't already):
```bash
git clone https://github.com/JeiHyde25/jeihyde-proj.git
cd coffee_sales_forecast
```

2. Set up Kaggle credentials:
- Copy your `kaggle.json` file to the project directory
- The file will be mounted into the container

3. Build and run the Docker container:
```bash
# Build the Docker image
docker build -t coffee-sales-forecast .

# Run the container
docker run -p 8501:8501 -v $(pwd)/kaggle.json:/root/.kaggle/kaggle.json coffee-sales-forecast
```

4. Access the application:
Open your web browser and navigate to `http://localhost:8501`

The application will open in your default web browser with the following features:
- View historical sales data and trends
- Make predictions for specific dates
- Generate future sales forecasts
- View model performance metrics
- Export predictions to CSV

## Model Performance
The model's performance metrics are displayed in the web interface and include:
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- R-squared Score

## Deployment
The application is deployed on Render.com and can be accessed at [https://coffee-forecast-app.onrender.com](https://coffee-forecast-app.onrender.com).

### Deployment Notes
- The app is deployed using Render's Web Service
- Free tier deployment may have cold starts (initial load might take a few seconds)
- The deployment automatically pulls from the main branch of the repository
- Environment variables are configured through Render's dashboard

### Local vs Deployed Version
- The deployed version has the same functionality as the local version
- All features including predictions, visualizations, and data exports are available
- The deployed version uses the same model and data processing pipeline

## Troubleshooting

### Docker Issues
- If you get permission errors with Kaggle credentials, make sure your `kaggle.json` file has the correct permissions
- If the container fails to start, check if port 8501 is already in use
- For Windows users, use `%cd%` instead of `$(pwd)` in the docker run command

### Kaggle Authentication
- Ensure your `kaggle.json` file contains valid credentials
- The file should be properly mounted in the Docker container
- Check the Kaggle API status if downloads fail