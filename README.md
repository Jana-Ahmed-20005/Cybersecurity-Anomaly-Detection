# 🛡️ Cybersecurity Threat Detection and Classification using Machine Learning

## 📚 Overview

This repository contains the work for a **two-phase machine learning project** focused on **network threat detection and classification**. In **Phase 1**, we developed a binary classification system to detect whether a network connection is normal or malicious. In **Phase 2**, we extended the system into a **multiclass classifier** to identify the specific type of cyberattack such as DDoS, DoS, Reconnaissance, MITM, and Mirai.

---

## 👥 Team Information


- **Members:**
  - Ahmed Mohsen (Me)
  - [Jana Ahmed (@Jana-Ahmed-20005)](https://github.com/Jana-Ahmed-20005) 
  - [Ali Elrouby (@AliElrouby)](https://github.com/AliElrouby)
  - [Mazen Ahmed (@Mazen-980)](https://github.com/Mazen-980)

---

## 📌 Phase 1: Binary Threat Detection

### 🔍 Problem Statement

Design a system to detect whether a network connection is **safe (normal)** or **dangerous (anomaly)** based on data collected from a **military network**. The data initially included only anomalies, which posed challenges due to **class imbalance**.

---

### 📊 Dataset Exploration

- **Rows:** 14,036
- **Columns:** 31 (15 float, 12 int, 4 string)
- **Issues Identified:**
  - Severe class imbalance
  - No null values or duplicates
- **Techniques Used:**
  - Histograms, Boxplots, Scatterplots
  - Correlation Matrix Analysis
  - Feature Selection (Top 20 by correlation)

---

### 🛠️ Data Preprocessing

- **Label Encoding** for categorical features
- **RobustScaler** to handle skewed distributions
- **Train-Validation-Test Split** to avoid data leakage
- **Feature Selection** for top 20 relevant features

---

### 🧠 Models Implemented

| Model              | Accuracy (Before SMOTE) | Accuracy (After SMOTE) | Accuracy (After NearMiss) |
|-------------------|--------------------------|--------------------------|----------------------------|
| K-Nearest Neighbors (KNN) | 0.9964 | 0.9886 | 0.5949 |
| Ridge Regression   | 0.9882 | 0.9586 | 0.7207 |
| Logistic Regression| 0.9615 | 0.9601 | 0.6172 |
| SVM (RBF)          | 0.9882 | 0.9890 | 0.5807 |
| Decision Tree      | 0.9921 | 0.9843 | 0.6016 |
| Random Forest      | 0.9967 | 0.9966 | 0.5826 |

---

### 🧪 Ensembling Techniques

| Technique       | Accuracy  |
|----------------|-----------|
| Soft Voting     | 0.9957    |
| Hard Voting     | 0.9960    |
| Stacking        | 0.9971    |
| Bagging         | 0.9971    |

---

### 🔁 Sampling Techniques

- **SMOTE (Oversampling):** Applied to training data only; improved accuracy and reduced overfitting.
- **NearMiss (Undersampling):** Balanced class count but reduced performance significantly.

---

### 📈 Hyperparameter Tuning

- Manual search, loop-based plotting, and graph comparison.
- Best parameters identified for each classifier.

---

### ✅ Phase 1 Conclusion

- **Best Model:** Random Forest after SMOTE
- **Best Accuracy:** 0.9966
- **Main Challenges:**
  - Severe class imbalance
  - Feature variability

---

## 🛡️ Phase 2: Attack-Type Classification

### 🔍 Problem Statement

In this phase, the goal was to detect not just if the connection is malicious, but also to **classify the type of attack** into one of the following:

- BenignTraffic
- DDoS
- DoS
- Recon
- MITM
- Mirai

---

### 📊 Dataset Exploration

- **Features:** 21 numeric/binary features
- **Target Classes:** 6
- **Key Steps:**
  - `.describe()` for distribution analysis
  - Histogram and correlation heatmaps
  - Identified duplicate column (`overall_rate`)
  - Checked for nulls and duplicates

---

### 🛠️ Preprocessing & Feature Engineering

- **Logarithmic Scaling:** Applied via `log1p()` to mitigate skewness.
- **Feature Creation (12 engineered features):**
  - Rate ratio, Rate sum, Flow time per byte
  - Duration per rate, Total flags, Is flag heavy
  - Is TCP heavy, Is UDP slow, Rate diff, etc.
- **Label Encoding** of target variable

---

### 🧠 Models Tried

- KNN
- Logistic Regression (OvR)
- SVM
- Decision Tree
- Random Forest
- MLP (Neural Network)
- XGBoost
- LightGBM
- CatBoost

---

### 🧪 Ensemble Learning

- **Soft Voting**
- **Stacking**
  - Base: LightGBM + Random Forest
  - Meta: Logistic Regression (One-vs-Rest)

---

### 🔍 Hyperparameter Tuning Techniques

- Manual tuning
- `RandomizedSearchCV`
- **Optuna** (automated hyperparameter optimization)

---

### 🎯 Evaluation Metrics

| Model              | Accuracy       |
|-------------------|----------------|
| LightGBM          | 91.45%         |
| Random Forest     | 91.12%         |
| Final Stacked     | **91.51%** ✅  |

---

### ✅ Phase 2 Conclusion

- Successfully created a robust **multiclass classifier** for identifying specific cyberattacks.
- Final model (stacked ensemble) delivered **91.51% accuracy**.
- Useful for **automated network defense systems**.

---

## 🧪 Tools and Libraries

- Python (Scikit-learn, Pandas, NumPy, Matplotlib, Seaborn)
- LightGBM
- XGBoost, CatBoost
- Optuna
- SMOTE (Imbalanced-learn)

---
## 📜 Final Notes

This project presents a **complete pipeline** for handling a real-world cybersecurity detection problem—from binary classification to detailed multiclass attack labeling. The combination of **rigorous preprocessing, thoughtful feature engineering, multiple ML models, and careful evaluation** ensures the robustness and applicability of the developed solution.

