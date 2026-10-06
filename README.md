# 🏷️ Tokped-Price-Predictor — E-Commerce Price Prediction

> Machine learning web application for predicting **Tokopedia** product prices based on product titles, categories, and descriptions using **TF-IDF** and **Linear Regression**.

---

## 📌 Features
- **NLP Text Representation**: Extracts salient keywords and features from Indonesian product titles via `tfidf.pkl`.
- **Regression Model**: Predicts fair market price using a trained `model_linreg.pkl`.
- **Web Interface**: Simple Flask UI (`app.py` + `templates/index.html`) for instant price estimation.

---

## 🛠️ Tech Stack
- **Machine Learning**: Scikit-Learn, Pandas, NumPy
- **NLP**: TF-IDF Vectorizer
- **Backend**: Flask
- **Deployment**: Procfile configured

---

## 🚀 Quick Start

```bash
git clone https://github.com/MasterPandaa/Tokped-Price-Predictor.git
cd Tokped-Price-Predictor
pip install -r requirements.txt
python app.py
```
Open [http://localhost:5000](http://localhost:5000) to test predictions.
