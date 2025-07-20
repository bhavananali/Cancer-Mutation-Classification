# 🧬 Cancer Mutation Classification - MSKCC Challenge

This project addresses the **MSKCC: Redefining Cancer Treatment** challenge hosted on [Kaggle](https://www.kaggle.com/c/msk-redefining-cancer-treatment/). The goal is to **automate the classification of genetic mutations** using clinical text data and expert annotations, thereby contributing to the development of precision medicine.

---

## 🏥 Problem Statement

Given a dataset of genetic mutations and associated clinical literature, classify each mutation into one of **nine classes** based on its relevance and role in cancer. This automates a task that is currently done manually by clinical pathologists.

---

## 🧠 Motivation

Identifying **driver mutations** (those contributing to tumor growth) from **passenger mutations** (those with no effect) is critical for developing personalized treatments. This classification:
- Is time-consuming if done manually.
- Requires interpretability and accuracy.
- Demands reliable probabilistic predictions for clinical relevance.

---

## 📂 Dataset

**Source**: [Kaggle MSKCC Dataset](https://www.kaggle.com/c/msk-redefining-cancer-treatment/data)

Two files are provided:

- `training_variants.csv`  
  Columns: `ID`, `Gene`, `Variation`, `Class` (1-9)

- `training_text.csv`  
  Columns: `ID`, `Text` (text-based clinical literature for the mutation)

Both files are joined using the `ID` column.

---

## 🔍 Business and ML Objectives

### Business Objectives:
- Automate classification to reduce human effort.
- Support clinicians with interpretable models.
- Ensure reliable probability outputs for decision making.

### Constraints:
- No low-latency requirement.
- Model interpretability is important.
- Minimize probabilistic errors (penalized via log-loss).

---

## 🤖 Machine Learning Formulation

- **Type**: Multi-class Classification (9 classes)
- **Features**: Text (clinical evidence), Gene name, Variation
- **Label**: Class (1-9)
- **Performance Metric**:
  - Multi-class Log Loss
  - Confusion Matrix (for class-wise performance)

---

## 🧪 Data Split

The dataset is split into:
- **Training set**: 64%
- **Cross-validation set**: 16%
- **Test set**: 20%

---

## 🛠️ Approach

1. **Data Preprocessing**  
   - Merge both CSVs on `ID`
   - Clean and tokenize clinical text
   - Encode categorical features (`Gene`, `Variation`)

2. **Feature Engineering**  
   - TF-IDF vectorization of clinical text
   - Combine TF-IDF with one-hot/categorical features

3. **Modeling**  
   Explored and compared multiple ML models:
   - Naive Bayes
   - Random Forest
   - Gradient Boosting (XGBoost)
   - Support Vector Machine (SVM)
   - **Logistic Regression** (performed best)

   ✅ **Logistic Regression achieved the lowest log-loss of 1.143** among all models.

4. **Evaluation**  
   - Assessed using log-loss and confusion matrix
   - Visualized misclassifications and class probabilities

---

## 📈 Results

- Best Performing Model: **Logistic Regression**
- Evaluation Metric: **Multi-class Log Loss = 1.143**
- Logistic Regression outperformed other classifiers in terms of log-loss while maintaining good interpretability.

---

## 🛠 Tech Stack

- Python 3.x
- Scikit-learn
- Pandas, NumPy
- NLTK / spaCy
- Matplotlib / Seaborn

---

## 🧾 Citation

Kaggle Competition:  
📎 https://www.kaggle.com/c/msk-redefining-cancer-treatment/

Memorial Sloan Kettering Cancer Center (MSKCC)

---

## 🙋‍♀️ Author

**Nali Bhavana**  
MTech in AI, IIT Bhubaneswar  
GitHub: [@bhavananali](https://github.com/bhavananali)

---
