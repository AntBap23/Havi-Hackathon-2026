# 🍔 QSR Demand Forecasting Platform

> A machine learning forecasting platform developed for the HAVI x Northern Illinois University Hackathon to predict restaurant demand using historical sales, weather, promotions, holidays, and calendar effects.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-ML-green?style=for-the-badge)
![Scikit Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)

---

# Overview

Accurate demand forecasting is one of the most important challenges in supply chain and restaurant operations.

Overestimating demand increases food waste and inventory costs, while underestimating demand leads to stockouts, lost revenue, and poor customer experiences.

This project was developed during the **HAVI x Northern Illinois University Demand Forecasting Hackathon**, where our team built a machine learning forecasting pipeline capable of predicting daily menu item demand across multiple restaurants.

Our solution combined feature engineering, exploratory analysis, time-series validation, and gradient boosting models to generate demand forecasts optimized for business performance.

🥈 **2nd Place Overall**

---

# Business Problem

Quick Service Restaurants (QSRs) require highly accurate demand forecasts to support inventory planning and operational efficiency.

Traditional forecasting methods often struggle to capture changing customer behavior caused by:

- Promotions
- Holidays
- Weather
- Local events
- Seasonal demand
- Restaurant-specific purchasing patterns

The objective was to build a forecasting model capable of accurately predicting daily demand while minimizing forecasting error using the competition's evaluation metric.

---

# Project Objective

Forecast daily demand for every:

- Restaurant
- Menu Item
- Date

across the official competition holdout period.

Forecast Window

**October 1, 2025 – December 31, 2025**

Total Predictions

**69,000 forecasts**

Evaluation Metric

**Weighted Mean Absolute Percentage Error (wMAPE)**

Lower scores indicate more accurate business forecasts.

---

# Solution Architecture

```
Historical Restaurant Data
        │
        ▼
Data Cleaning & Validation
        │
        ▼
Exploratory Data Analysis
        │
        ▼
Feature Engineering
        │
        ▼
Time-Based Train / Validation Split
        │
        ▼
LightGBM Forecasting Model
        │
        ▼
Performance Evaluation
        │
        ▼
Submission Generation
```

---

# Dataset

The forecasting dataset contains approximately **1.37 million historical observations** covering multiple years of restaurant operations.

The data includes:

- Daily sales
- Restaurant information
- Menu items
- Weather
- Holidays
- Promotions
- Calendar features
- Local events

Each observation represents a single menu item sold at a specific restaurant on a specific day.

---

# Machine Learning Pipeline

## Exploratory Data Analysis

Initial analysis focused on understanding demand behavior through:

- Sales distributions
- Seasonal trends
- Restaurant comparisons
- Category performance
- Missing value analysis
- Feature relationships

---

## Feature Engineering

Features were engineered to capture historical purchasing behavior while avoiding data leakage.

Examples include:

- Lag features
- Rolling averages
- Calendar variables
- Holiday indicators
- Weather effects
- Promotional activity
- Restaurant characteristics

---

## Model Development

The primary forecasting model used **LightGBM**, a gradient boosting framework well suited for structured business data.

The model was selected because it:

- Handles nonlinear relationships
- Captures feature interactions
- Performs well on tabular datasets
- Trains efficiently
- Provides feature importance for model interpretation

---

## Validation Strategy

Rather than randomly splitting the data, the project used **time-based validation** to better simulate real-world forecasting.

This approach ensures future observations are never used during model training, preventing information leakage.

Validation emphasized business realism over maximizing leaderboard performance.

---

# Results

🏆 **2nd Place — HAVI x NIU Demand Forecasting Hackathon**

Key accomplishments included:

- End-to-end forecasting workflow
- Robust feature engineering
- Time-aware validation
- Business-focused evaluation
- High-performing LightGBM model

Performance was measured using **wMAPE**, a metric commonly used in supply chain planning because it prioritizes errors on high-volume products.

---

# Visualizations

The repository includes visualizations for:

- Feature Importance
- Actual vs Predicted Demand
- Residual Analysis
- Category Performance
- Restaurant Performance
- Forecast Accuracy

These analyses helped identify where the model performed well and where additional feature engineering could improve forecasts.

---

# Repository Structure

```
Havi-Hackathon-2026/

├── data/
│
├── models/
│
├── charts/
│
├── docs/
│
├── notebooks/
│
├── reports/
│
├── requirements.txt
│
└── README.md
```

---

# Skills Demonstrated

- Machine Learning
- Forecasting
- Feature Engineering
- Time Series Validation
- Supply Chain Analytics
- Predictive Modeling
- Python
- Pandas
- LightGBM
- Business Analytics
- Data Visualization
- Model Evaluation

---

# Lessons Learned

This project strengthened my understanding of production-style forecasting workflows, including:

- Designing realistic validation strategies
- Preventing data leakage
- Building interpretable machine learning models
- Engineering business-driven features
- Evaluating models using operational metrics
- Translating forecasting results into business recommendations

---

# Future Improvements

Potential enhancements include:

- Hyperparameter optimization with Optuna
- Model ensembling
- Hierarchical forecasting
- Deep learning forecasting models
- Automated retraining pipeline
- MLflow experiment tracking
- Cloud deployment
- Interactive forecasting dashboard

---

# About Me

I'm passionate about solving business problems using analytics, experimentation, AI, and machine learning.

My interests include:

- Product Analytics
- Forecasting
- Supply Chain Analytics
- AI-powered Decision Support
- Analytics Engineering
- Experimentation

Feel free to connect if you'd like to discuss forecasting, analytics engineering, or machine learning.

---

## License

MIT License
