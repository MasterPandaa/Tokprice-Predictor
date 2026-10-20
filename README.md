# Tokprice-Predictor — E-Commerce Sales & Pricing Estimation Engine

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB.svg?logo=python&logoColor=white)](#)
[![Flask](https://img.shields.io/badge/Flask-2.x-000000.svg?logo=flask&logoColor=white)](#)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-ML%20Pipeline-F7931E.svg?logo=scikit-learn&logoColor=white)](#)
[![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-3.x-38B2AC.svg?logo=tailwind-css&logoColor=white)](#)
[![Explainable AI](https://img.shields.io/badge/XAI-Feature%20Impact%20Analysis-8B5CF6.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](#)

A machine learning web application for estimating product sales volume and evaluating pricing strategies for Tokopedia e-commerce listings.

Tokprice-Predictor integrates regularized linear regression (**Ridge Regression**), numeric feature normalization (**StandardScaler**), NLP text feature extraction (**TF-IDF Vectorizer**), and **Explainable AI (XAI)** visualizations to inspect how listing attributes influence transaction volume.

---

## Overview

Setting optimal prices and discounts on e-commerce platforms requires balancing margins against visibility and sales velocity. Tokprice-Predictor analyzes listing factors to project sales volume based on patterns trained on marketplace transaction data:

- **Multimodal Feature Processing**: Concurrently ingests pricing metrics (base price, discount, final price), merchant ratings, review volume, and product title semantics.
- **Explainable Feature Contribution**: Deconstructs each prediction into positive drivers versus limiting factors (e.g., impact of pricing tier vs. review count).
- **In-Memory Visualization**: Generates SHAP-inspired feature impact waterfall charts in backend memory, delivered as Base64 images without disk I/O overhead.
- **Sanitization & Input Validation**: Validates pricing sanity and flags edge cases (e.g., title length extremes or abnormal rating-to-review ratios).

---

## Technical Pipeline

1. **Text Preprocessing & TF-IDF Extraction**: Cleans Indonesian product title strings (`clean_text` regex pipeline) and generates n-gram term frequencies.
2. **Numeric Feature Scaling**: Standardizes price points, discount percentages, ratings, and log-transformed review volumes.
3. **Ridge Regression Estimator**: Regularized $L_2$ regression calibrated to minimize RMSE ($R^2 \approx 0.78$) while avoiding overfitting to high-volume outlier listings.
4. **Flask Web Dashboard**: Responsive interface built with Tailwind CSS, delivering instant estimations and diagnostic metrics.

---

## Getting Started

### Prerequisites

- Python 3.9+
- pip & virtualenv

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/MasterPandaa/Tokprice-Predictor.git
   cd Tokprice-Predictor
   ```

2. **Create and activate a virtual environment**:
   ```bash
   # Windows
   python -m venv venv
   .\venv\Scripts\activate

   # Linux / macOS
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application**:
   ```bash
   python app.py
   ```
   Open `http://127.0.0.1:5000` in your browser.

---

## Project Structure

```text
Tokprice-Predictor/
├── app.py                      # Flask web application & inference router
├── requirements.txt            # Python dependencies
├── model/                      # Serialized scikit-learn models & vectorizers
│   ├── ridge_model.pkl
│   ├── tfidf_vectorizer.pkl
│   └── scaler.pkl
├── templates/                  # Jinja2 HTML templates styled with Tailwind CSS
├── static/                     # Static assets, scripts, and styling
├── Procfile                    # WSGI configuration (Gunicorn) for cloud deployment
└── README.md                   # Project documentation
```

---

## License

This project is licensed under the [MIT License](LICENSE).
