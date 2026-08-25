# ✈️ Airline Customer Loyalty Prediction & WLI
### AI-Driven Loyalty Intelligence & Strategic Service Recovery

<p align="center">
<img src="https://img.shields.io/badge/Python-3.9+-blue?style=for-the-badge&logo=python">
<img src="https://img.shields.io/badge/LightGBM-Efficiency-EB912E?style=for-the-badge">
<img src="https://img.shields.io/badge/NLP-Sentiment%20Analysis-8E44AD?style=for-the-badge">
<img src="https://img.shields.io/badge/Metric-WLI%20Index-00A8E8?style=for-the-badge">
<img src="https://img.shields.io/badge/Framework-Scikit--Learn-F7931E?style=for-the-badge&logo=scikitlearn">
</p>

---

## 📌 Project Overview

Customer loyalty is the ultimate differentiator in the aviation industry. Traditional metrics like NPS often fail to capture the "Why" behind passenger behavior. 

This project introduces a scalable **Loyalty Intelligence System** that predicts promoter behavior and generates a unified **Weighted Loyalty Index (WLI)**. By blending machine learning with sentiment depth, it converts subjective reviews into actionable strategic insights.

---

## ⭐ Key Innovation: Weighted Loyalty Index (WLI)

The **WLI** is a multi-dimensional KPI designed to offer a 360-degree view of passenger loyalty:

$$WLI_{Score} = (W_1 \cdot NPS_{Score}) + (W_2 \cdot Sentiment_{Depth}) + (W_3 \cdot Service_{Actionability})$$

### 🔹 Component Breakdown:
* **NPS Score (0–1):** Normalized rating derived from the 10-point scale.
* **Sentiment Depth:** Measures emotional quality using Cabin Staff Service (CSS) and Inflight Entertainment (IE).
* **Service Actionability:** Feature-weighted diagnostic using **LightGBM** importance scores.

---

## 📂 Dataset Summary

**Source:** Airline Industry Reviews (Kaggle) | **Records:** 23,171

| Feature | Description | Type |
| :--- | :--- | :--- |
| **Overall Rating** | 1–10 passenger rating | Numeric |
| **Review** | Full text feedback (Sentiment source) | Text |
| **Service Ratings** | 1-5 stars (Seat, Food, Wifi, etc.) | Float |
| **Recommended** | Binary Target (Promoter proxy) | Boolean |

---

## 🛠️ Methodology

### 1️⃣ Data Engineering
* **Cleaning:** Missing value imputation and standardization of service ratings.
* **Text Processing:** Tokenization, Lemmatization, and TF-IDF Vectorization for review analysis.

### 2️⃣ Hybrid Feature Engineering


[Image of machine learning feature engineering process]

* Integration of **Metadata** (Seat Type, Traveller Type), **Numerical Ratings**, and **Text Vectors** into a unified feature matrix.

### 3️⃣ Model Architecture
* **Champion Model:** LightGBM Classifier.
* **Objective:** Maximize prediction accuracy and extract feature importance for WLI weighting.

---

## 📊 Model Evaluation

| Metric | Score |
| :--- | :--- |
| **Precision (Promoters)** | **0.94** |
| **Recall (Promoters)** | **0.94** |
| **F1-Score** | **0.94** |
| **Overall Accuracy** | **0.96** |

---

## 🔍 Key Insights

* **⚠️ Data Integrity:** "Missing Seat Type" emerged as the largest loyalty risk factor.
* **💬 Emotional Drivers:** Keywords like *excellent* and *great* are high-confidence predictors of promoters, while *worst* and *hour* signal immediate churn risk.
* **✨ Service Quality:** Cabin Staff Service (CSS) has the highest correlation with high WLI scores.

---

## 🚀 Strategic Recommendations

1.  **Fix Data Gaps:** Audit missing "Seat Type" entries to improve loyalty tracking accuracy.
2.  **Reinforce Positives:** Use the model to identify "Promoter Behaviors" and train staff to replicate them.
3.  **Real-Time Recovery:** Deploy the classifier to flag negative reviews instantly for customer service follow-up.
4.  **Resource Allocation:** Use WLI to prioritize investments in service areas with the highest "Actionability" weight.

---

## Engineering Decisions & Challenges Solved

| Challenge | Decision | Why |
|---|---|---|
| Mixed-language reviews (Arabic + English) | Language detection + separate sentiment pipelines per language | Arabic sentiment models differ from English ones; mixing them degrades accuracy |
| Noisy customer reviews with slang, typos, emojis | Text cleaning pipeline: lowercase, special char removal, lemmatization | Raw review text is extremely noisy — cleaning improves signal-to-noise ratio for the classifier |
| Feature importance not obvious from raw text | TF-IDF vectorization with n-grams (unigram + bigram) | Bigrams capture phrases like "not good" that unigrams miss — critical for sentiment accuracy |
| Different airlines have different review distributions | Per-airline baseline comparison before aggregated analysis | Comparing Emirates to a budget airline without normalizing for service tier is misleading |

## 👨‍💻 Author

**Narendra Gandikota (G‑Narendra)** AI | ML | Python | GenAI Enthusiast  

GitHub: [https://github.com/G-Narendra](https://github.com/G-Narendra)
