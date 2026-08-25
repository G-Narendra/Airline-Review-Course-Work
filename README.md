# ✈️ Airline Customer Loyalty Prediction & WLI

**Multi-model classification for airline loyalty prediction with Weighted Loyalty Index (WLI) calculation.**

[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/)
[![LightGBM](https://img.shields.io/badge/LightGBM-EB912E.svg)](https://lightgbm.readthedocs.io/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2EAD33.svg)](https://xgboost.readthedocs.io/)
[![License MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

---

## 🎯 Problem Statement

Airlines collect thousands of customer reviews but struggle to quantify loyalty beyond simple star ratings. A 5-star review from a frequent business traveler carries different weight than a 5-star review from a one-time tourist. Existing loyalty metrics (NPS, CSAT) treat all reviews equally and miss the nuanced relationship between service quality, sentiment depth, and actual loyalty behavior.

The challenge is to build a predictive model that classifies customer loyalty and derives a Weighted Loyalty Index (WLI) that captures three dimensions: NPS-like score (overall rating), sentiment depth (emotional engagement), and service actionability (which service aspects drive loyalty most).

---

## 📊 What I Built

A complete ML pipeline with model comparison and loyalty index calculation:

1. **Data Loading**: Load airline review dataset from Google Colab
2. **Text Preprocessing**: TF-IDF vectorization with n-grams (1,2), stopwords removal, lemmatization
3. **Hybrid Feature Engineering**: Combine text features (TF-IDF) + categorical features (OneHotEncoder) + service rating columns
4. **Model Training**: Compare 3 models:
   - **LightGBM** (primary, used for WLI weights)
   - **Logistic Regression** (baseline)
   - **XGBoost** (alternative)
5. **WLI Calculation**: Use LightGBM feature importance as weights for Service_Actionability component
6. **Time Series Analysis**: Monthly WLI trend analysis
7. **Insight Extraction**: Top 20 predictors from feature importance

### Key Results

| Model | Purpose |
|---|---|
| **LightGBM** | Primary model, used to derive WLI weights via feature importance |
| **Logistic Regression** | Baseline comparison |
| **XGBoost** | Alternative ensemble comparison |

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| **Language** | Python 3.9+ |
| **Data Processing** | Pandas, NumPy |
| **NLP** | NLTK (stopwords, lemmatization), TF-IDF |
| **ML Frameworks** | LightGBM, XGBoost, Scikit-Learn |
| **Visualization** | Matplotlib, Seaborn |
| **Environment** | Google Colab |

---

## 📁 Project Structure

```
Airline-Review-Course-Work/
├── AirLines Review Code.ipynb      # Main notebook with full pipeline
├── README.md
└── LICENSE
```

---

## 🔧 How to Run

```bash
# Install dependencies
pip install pandas numpy scikit-learn lightgbm xgboost nltk

# Run in Google Colab (recommended for Google Drive integration)
# Or locally:
jupyter notebook "AirLines Review Code.ipynb"
```

---

## 🧪 Engineering Decisions

| Decision | Rationale |
|---|---|
| **LightGBM as primary model** | Faster training, handles mixed feature types well, provides feature importance for WLI calculation |
| **Hybrid feature engineering** | Combines text (TF-IDF) + categorical (OneHot) + numerical (service ratings) for richer signal |
| **TF-IDF with n-grams (1,2)** | Captures both unigrams and bigrams for better text representation |
| **WLI as weighted sum** | Three equal weights (NPS, Sentiment, Service) provide interpretable loyalty metric |
| **Feature importance as WLI weights** | Data-driven weights rather than arbitrary assumptions — model tells us which services matter most |

---

## ⚠️ Limitations

- **No cross-validation**: Uses single train/test split (80/20)
- **No confidence intervals**: Model predictions lack uncertainty quantification
- **Google Drive dependency**: Data loading requires Google Drive mount
- **Limited to airline domain**: WLI calculation is specific to airline service metrics
- **No temporal validation**: Time series analysis doesn't use walk-forward validation

---

## ⚠️ Disclaimer

This is an educational project for learning ML concepts. It is not intended for production use in airline operations.

---

*Built as part of MSc Data Science coursework — demonstrating multi-model comparison and custom loyalty index calculation.*
