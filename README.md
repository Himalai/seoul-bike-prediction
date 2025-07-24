# 🚲 Seoul Bike-Sharing Demand Prediction

This project predicts bike-sharing demand in Seoul using real-time weather forecasts and regression models. The goal is to help city planners and operators optimize bike availability based on temperature, humidity, wind speed, visibility, and seasonal patterns.

---


## 📁 Project Structure
seoul-bike-prediction/
├── 01_scraping_cleaning.Rmd # Data scraping, cleaning, and preprocessing
├── 02_analysis_modeling.Rmd # EDA, model training, and evaluation
├── shiny/ # Shiny dashboard app files
│ ├── app.R # Combined Shiny app (UI + server)
│ └── model_prediction.R # Logic to integrate weather forecast + prediction
├── model.csv # Final model coefficients used in prediction
├── selected_cities.csv # Cities used for dashboard forecast
├── model_comparison.csv # RMSE, R², MAE results for all models
├── final_predictions.csv # Final predicted values using best model
├── plots/ # All saved model & EDA plots (.png/.csv)
├── LICENSE # License for use and reuse
├── report.pdf # Final rendered PDF report (optional)
└── README.md # This file (project summary + instructions)

## ⚙️ Project Workflow

This is the sequence followed in the project:

1. **Data Collection**: Scraped weather and bike-sharing data from public sources.
2. **Data Cleaning**: Removed missing values, standardized columns, and normalized formats (`01_scraping_cleaning.Rmd`).
3. **Feature Engineering**: Created dummy variables for seasons and hours, and merged weather with bike demand data.
4. **EDA & Visualization**: Explored relationships between weather and demand using plots (`02_analysis_modeling.Rmd`).
5. **Modeling**: Used linear, Lasso, and Elastic Net regression to predict demand.
6. **Model Evaluation**: Compared models using MAE, RMSE, and visual diagnostics.
7. **Shiny Dashboard**: Built an interactive dashboard to forecast bike demand using real-time weather (in `shiny/`).


---

## 📦 Dataset

- **Seoul Bike Sharing Data**: Available from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Seoul+Bike+Sharing+Demand)
- **Weather Data**: Fetched from [OpenWeatherMap API](https://openweathermap.org/api) using real-time city-level forecasts

---

## 🔍 Steps Performed

1. **Scraping & Cleaning**:
   - Loaded and cleaned raw Seoul bike-sharing data
   - Normalized and exported clean CSVs for modeling

2. **EDA & Visualization**:
   - Explored temperature, humidity, and time-based trends
   - Created visual plots (e.g., bike vs. temp)

3. **Modeling & Evaluation**:
   - Linear, Polynomial, Lasso, and Elastic Net regression models
   - Evaluated using RMSE, MAE, MAPE, and R²
   - Selected the best model based on performance

4. **Forecast Integration**:
   - Integrated OpenWeatherMap forecast for selected global cities
   - Used final model to predict future bike demand per city

5. **Dashboard**:
   - Built an interactive `Shiny` dashboard to:
     - Select city
     - View predicted demand
     - Visualize temp, humidity, and model outputs on a map

---

## 🧪 How to Reproduce

1. Clone this repo:
   ```bash
   git clone https://github.com/<your-username>/seoul-bike-prediction.git
   cd seoul-bike-prediction

install.packages(c("tidyverse", "leaflet", "httr", "fastDummies", "shiny"))

shiny::runApp("shiny/")
