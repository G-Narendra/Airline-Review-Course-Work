# ✈️ Airline Customer Loyalty Prediction & Weighted Loyalty Index (WLI)
### **By: Narendra Gandikota**

---

## 📌 Project Overview
Customer loyalty is one of the most critical competitive differentiators in the aviation industry. Traditional metrics like NPS or star ratings often fail to reveal why passengers feel dissatisfied or what truly drives loyalty.

This project builds a scalable, data-driven loyalty intelligence system that identifies the root causes of customer dissatisfaction, predicts promoter behavior, and generates a unified loyalty metric — the **Weighted Loyalty Index (WLI)** — to guide strategic service improvements and real-time recovery actions.

---

## ⭐ Key Innovation: Weighted Loyalty Index (WLI)

The WLI is the project’s primary KPI — a unified loyalty score that blends three strategic pillars:

- **NPS Score (Loyalty Signal)**
- **Sentiment Depth (Emotional Context)**
- **Service Actionability (Data-Driven Diagnostic)**

---

## ✅ WLI Formula





WLI_Score= (W1_NPS x NPS Score)+
                        (W2_SENTIMENT x SentimentDepth)+
                        (W3_SERVICE x Service Actionability)




### 🔹 NPS Score (0–1 scale)


NPS Score=(Rating_i)/10



### 🔹 Sentiment Depth (Emotional Service Quality)
Uses Cabin Staff Service (CSS) and Inflight Entertainment (IE):



Sentiment Depth_i=(1/5) x ((CSS_i+IE_i)/2)


### 🔹 Service Actionability (Feature-Weighted Diagnostic)
Weights derived from LightGBM feature importance:



Service Actionablity_i=(∑_j(Rating_i ,_j x W_j ) )/(∑_j(5 x W_j ) )

---

## ✅ Why WLI Matters
- Converts subjective feedback into a single actionable metric  
- Helps managers prioritize service investments  
- Enables real-time service recovery  
- Identifies true loyalty drivers using machine learning  

---

## 📂 Dataset Summary

**Source:** Airline Industry Reviews (Kaggle)  
**Total Records:** 23,171  
**Includes:** Text reviews + 7 service ratings + metadata  

### **Key Attributes**

| Feature | Description | Type |
|--------|-------------|------|
| Airline Name | Airline reviewed | Object |
| Overall Rating | 1–10 rating | Object |
| Review Title | Short summary | Object |
| Review | Full text feedback | Object |
| Type of Traveller | Passenger type | Object |
| Seat Type | Travel class | Object |
| Seat Comfort | 1–5 rating | Float |
| Cabin Staff Service | 1–5 rating | Float |
| Food & Beverages | 1–5 rating | Float |
| Ground Service | 1–5 rating | Float |
| Inflight Entertainment | 1–5 rating | Float |
| Wifi & Connectivity | 1–5 rating | Float |
| Value for Money | 1–5 rating | Float |
| Recommended | Binary target | Object |

---

## 🛠️ Methodology

### ✅ 1. Data Cleaning & Standardization
- Removed rows with missing critical fields  
- Converted *Recommended* to binary  
- Standardized service ratings  
- Imputed missing values with 0  

### ✅ 2. Text Preprocessing
- Tokenization  
- Stopword removal  
- Lemmatization  
- TF-IDF vectorization  

### ✅ 3. Feature Engineering (Hybrid Approach)
Combined:
- One-hot encoded metadata  
- Numerical service ratings  
- TF-IDF text vectors  

→ Unified model-ready feature matrix  

### ✅ 4. Model Training
- **Champion Model:** LightGBM Classifier  
- **Target Variable:** `Recommended` (Promoter proxy)  
- **Objective:**  
  - Maximize prediction accuracy  
  - Extract feature importances for WLI’s Service Actionability  

---

## 📊 Model Evaluation

| Metric | Score |
|--------|--------|
| Precision (Promoters) | 0.94 |
| Recall (Promoters) | 0.94 |
| F1-Score | 0.94 |
| Overall Accuracy | 0.96 |

✅ Confirms model stability  
✅ Reliable promoter identification  
✅ Strong foundation for WLI weighting  

---

## 🔍 Results & Insights

### ✅ Model Performance
LightGBM outperformed XGBoost across all metrics:
- **Accuracy:** 92%  
- **F1-Score:** 0.94  
- **High precision & recall** → excellent promoter detection  

### ✅ Key Business Insights
- **Missing Seat Type** (importance: 128) → Largest loyalty risk → Data integrity issue  
- **Negative keywords:** *worst, poor, hour* → Strong indicators of dissatisfaction  
- **Positive keywords:** *excellent, great, thank you* → Strong predictors of promoter behavior  
- Emotional service quality (CSS + IE) strongly influences loyalty  

---

## ✅ Actionable Recommendations

### **1. Fix Data Integrity Issues**
- Audit and correct missing Seat Type entries  
- Highest-risk factor affecting loyalty  

### **2. Strengthen Positive Service Behaviors**
- Train staff to reinforce promoter-linked behaviors  
- Focus on empathy, attentiveness, and gratitude  

### **3. Deploy Real-Time Service Recovery**
- Use model predictions to flag negative reviews  
- Trigger immediate actions (apology, compensation, follow-up)  

### **4. Monitor Operational Risks**
- Track NPS dips during delay-heavy periods  
- Allocate resources proactively  

---

## 🚀 Conclusion
This project delivers a holistic loyalty intelligence framework that blends machine learning, sentiment analytics, and business strategy. The **Weighted Loyalty Index (WLI)** transforms fragmented customer feedback into a powerful, actionable metric that helps airlines:

- Improve customer retention  
- Enhance service quality  
- Prioritize investments  
- Respond to issues in real time  

It’s a scalable, data-driven approach to building stronger, more loyal customer relationships in the competitive airline industry.

