# CareAI — 30-Day Hospital Readmission Risk Prediction

> An end-to-end machine learning pipeline for predicting the risk of hospital readmission within 30 days using healthcare encounter data.

🚀 Overview

CareAI is a machine learning project built using the **Diabetes 130-US Hospitals** dataset from the UCI Machine Learning Repository.

The project compares multiple ML models, detects potential data leakage, optimizes the classification threshold, evaluates the final production model, and uses SHAP for explainability.

---

🔄 ML Pipeline

```text
Healthcare Dataset
       ↓
Exploratory Data Analysis
       ↓
Data Cleaning & Preprocessing
       ↓
Feature Engineering
       ↓
Train / Test Split
       ↓
Logistic Regression
       ↓
Random Forest
       ↓
XGBoost
       ↓
Model Comparison
       ↓
Feature Importance
       ↓
Data Leakage Detection
       ↓
Leakage Feature Removal
       ↓
Production XGBoost
       ↓
Threshold Optimization
       ↓
Model Evaluation
       ↓
SHAP Explainability
       ↓
Model & Results Saved
📊 Dataset
Diabetes 130-US Hospitals for Years 1999–2008
Total encounters: 101,766
Original features: 47
Production features: 46
Training samples: 81,412
Test samples: 20,354
Prediction Target
Binary classification of 30-day hospital readmission:
0 → Not readmitted within 30 days
1 → Readmitted within 30 days
🧠 Machine Learning
Models
Logistic Regression — baseline
Random Forest — ensemble comparison
XGBoost — production model
Preprocessing
Missing-value handling
Numerical feature scaling with StandardScaler
Categorical encoding with OneHotEncoder
Scikit-learn ColumnTransformer pipeline
🔍 Data Leakage Detection
Feature-importance analysis identified:
discharge_disposition_id
as a potential data-leakage feature.
It was removed from the production feature set to create a more realistic prediction pipeline.
🎯 Threshold Optimization
Instead of relying only on the default 0.50 classification threshold, multiple thresholds were evaluated.
The final production threshold was selected using F1-score optimization:
Final threshold: 0.15
This helps improve identification of potential readmission cases in the imbalanced dataset.
📈 Production Model Results
Production Model: XGBoost
Metric
Result
ROC-AUC
0.6606
Accuracy
0.78
Threshold
0.15
Readmission Precision
0.23
Readmission Recall
0.41
Readmission F1
0.30
Evaluation
The project generates:
Confusion Matrix
ROC Curve
Precision-Recall Curve
Accuracy
Precision
Recall
F1-score
ROC-AUC
🔬 SHAP Explainability
SHAP is used to understand how features influence XGBoost predictions.
Current analysis:
1,000 test samples
2,378 transformed features
SHAP summary visualization
Output:
evaluation/shap_summary.png
💾 Saved Artifacts
models/
└── careai_model_v1.joblib

evaluation/
├── confusion_matrix.png
├── roc_curve.png
├── precision_recall_curve.png
└── shap_summary.png

outputs/
├── evaluation_results.json
├── metrics.csv
└── prediction_examples.json
The trained production pipeline is saved using Joblib and healthcare data is stored using SQLite.
🛠️ Technologies & Tools
Language: Python
Machine Learning: Scikit-learn, XGBoost
Data Processing: Pandas, NumPy
Visualization: Matplotlib, Seaborn
Explainable AI: SHAP
Database: SQLite
Model Saving: Joblib
Environment: Google Colab, Jupyter Notebook
Version Control: Git, GitHub
▶️ How to Run
Google Colab
Open:
CareAI_ML_Risk_Prediction.ipynb
Install dependencies:
!pip install ucimlrepo shap xgboost scikit-learn pandas numpy matplotlib seaborn joblib -q
Then run the notebook from top to bottom.
Local
git clone https://github.com/srilakshmi005/careai-healthcare-ai.git
cd careai-healthcare-ai
pip install ucimlrepo shap xgboost scikit-learn pandas numpy matplotlib seaborn joblib
jupyter notebook
Open:
CareAI_ML_Risk_Prediction.ipynb
📁 Project Structure
careai-healthcare-ai/
│
├── CareAI_ML_Risk_Prediction.ipynb
├── README.md
├── LICENSE
│
├── evaluation/
│   ├── confusion_matrix.png
│   ├── roc_curve.png
│   ├── precision_recall_curve.png
│   └── shap_summary.png
│
├── models/
│   └── careai_model_v1.joblib
│
└── outputs/
    ├── evaluation_results.json
    ├── metrics.csv
    └── prediction_examples.json
⭐ Key Highlights
End-to-end healthcare ML pipeline
101K+ healthcare encounters
Multiple ML model comparison
XGBoost production model
Data leakage detection & removal
F1-based threshold optimization
ROC-AUC: 0.6606
Accuracy: 78%
SHAP model explainability
Reusable serialized ML pipeline
SQLite data storage
Reproducible Google Colab workflow
⚠️ Disclaimer
CareAI is an educational/research machine learning project and has not been clinically validated.
It should not be used for medical diagnosis, treatment decisions, or real-world clinical decision-making.
👩‍💻 Author
Srilakshmi Kummari
B.Tech — Electronics & Communication Engineering

**This is the version I recommend for your GitHub.** It looks much more like a professional ML portfolio project while still showing the important technical work you actually did.
