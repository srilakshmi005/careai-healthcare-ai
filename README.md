# careai-healthcare-ai
Production-ready Healthcare AI platform combining ML risk prediction, RAG, LLM evaluation, SQL, monitoring, and deployment.
# 🏥 CareAI — Healthcare 30-Day Readmission Risk Prediction

CareAI is an end-to-end Machine Learning system designed to predict the risk of hospital readmission within 30 days using publicly available, de-identified healthcare data.

The project includes data preprocessing, data leakage detection, model comparison, threshold optimization, SQL storage, prediction logging, monitoring, drift detection, FastAPI model serving, automated testing, and model versioning.

---

## 🎯 Project Objective

The objective of CareAI is to predict whether a patient is likely to be readmitted to a hospital within 30 days.

### Workflow

Healthcare Dataset → Data Inspection → Preprocessing → Leakage Detection → Model Training → Model Evaluation → Threshold Optimization → Production Model → FastAPI API → SQL Logging → Monitoring

---

## 📊 Dataset

CareAI uses the Diabetes 130-US Hospitals for Years 1999–2008 dataset from the UCI Machine Learning Repository.

- Total healthcare encounters: **101,766**
- Original features: **47**
- Production features: **46**
- Training records: **81,412**
- Testing records: **20,354**
- Prediction target: **30-day hospital readmission**

The dataset is publicly available and de-identified.

---

## 🤖 Machine Learning Models

| Model | ROC-AUC | Description |
|---|---:|---|
| Logistic Regression | 0.6440 | Baseline model |
| Random Forest | 0.6631 | Tree-based comparison |
| XGBoost | 0.6920 | Initial model with potential leakage |
| Production XGBoost | **0.6606** | Leakage-controlled model |

---

## 🔐 Data Leakage Detection

During feature-importance analysis, `discharge_disposition_id` was identified as a potentially unavailable feature at the intended prediction point.

The feature was removed from the production model.

### Before leakage removal

**XGBoost ROC-AUC:** 0.6920

### After leakage removal

**Production XGBoost ROC-AUC:** 0.6606

Although the ROC-AUC decreased, the production model provides a more defensible evaluation by excluding a potentially unavailable feature.

---

## 🏆 Production Model

- **Model Version:** `careai_xgboost_v1`
- **Algorithm:** XGBoost
- **Prediction Target:** 30-day readmission
- **Production Features:** 46
- **Training Rows:** 81,412
- **Testing Rows:** 20,354
- **ROC-AUC:** 0.6606
- **Decision Threshold:** 0.15

The trained model was saved using Joblib.

---

## ⚖️ Threshold Optimization

Multiple classification thresholds were evaluated using:

- Precision
- Recall
- F1-score

The selected development threshold is:

**0.15**

At threshold 0.15:

- Precision: **0.213**
- Recall: **0.347**
- F1-score: **0.264**

This demonstrates the trade-off between identifying potential readmissions and reducing false-positive predictions.

The threshold is for this educational project and has not been clinically validated.

---

## 🗄️ SQL Data Layer

CareAI uses **SQLite** for data storage and prediction logging.

The project created:

`careai_healthcare.db`

Prediction records include:

- Prediction ID
- Timestamp
- Model version
- Prediction
- Risk classification
- Probability
- Decision threshold

---

## 🌐 FastAPI Model Serving

The trained model is exposed through a FastAPI application.

### Health Endpoint

```text
GET /
Prediction Endpoint
POST /predict
The prediction API returns information such as:
Prediction
Risk classification
Probability
Decision threshold
Model version
🧪 Automated Testing
Automated API tests were implemented for:
Health endpoint
Prediction endpoint
Invalid input/error handling
Development testing completed successfully.
📈 ML Monitoring
CareAI includes basic monitoring for:
Prediction counts
High-risk predictions
Average prediction probability
Maximum prediction probability
Numeric feature distributions
Potential feature drift
The development monitoring result was:
No significant drift detected.
This monitoring implementation is a demonstration and is not a clinically validated monitoring system.
🔄 Model Versioning
Model metadata includes:
Project: CareAI
Model version: careai_xgboost_v1
Algorithm: XGBoost
Prediction target: 30-day readmission
Production features: 46
Training rows: 81,412
Testing rows: 20,354
ROC-AUC: 0.6606
Decision threshold: 0.15
Leakage feature removed: discharge_disposition_id
The project uses Joblib for model persistence and requirements.txt for dependency management.
🛠️ Technology Stack
Programming: Python
Data Processing: Pandas, NumPy
Machine Learning: Scikit-learn, XGBoost
Database: SQLite, SQL
API: FastAPI, Pydantic
Model Persistence: Joblib
Development: Google Colab, GitHub
📁 Project Structure
CareAI-ML-Risk-Prediction/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── CareAI_Development.ipynb
│
├── app/
│
├── tests/
│
└── monitoring/
🔬 ML Engineering Concepts Demonstrated
Python ML development
Data preprocessing
Missing-value analysis
Data leakage detection
Model comparison
XGBoost
Classification
ROC-AUC evaluation
Precision/Recall analysis
F1-score evaluation
Decision-threshold optimization
SQL data storage
Prediction logging
Model versioning
REST API development
FastAPI
Automated API testing
ML monitoring
Data drift detection
Reproducibility
🚀 Future Improvements
Docker containerization
Cloud deployment
CI/CD pipeline
MLflow experiment tracking
Advanced statistical drift detection
Fairness evaluation
Production observability
Structured application logging
Cloud-based model serving
RAG-based healthcare assistant
LLM evaluation
AI guardrails
🔒 Data Privacy & Safety
CareAI does not connect to a real hospital system.
The project uses publicly available, de-identified research data.
No private hospital database or real-time patient information is used.
CareAI is an educational/research project and has not been clinically validated.
The predictions must not be used to make real-world patient-care decisions.
👩‍💻 Author
Srilakshmi Kummari
B.Tech Graduate | AI/ML & Software Engineering
⭐ Project Highlights
Component
Result
Healthcare encounters
101,766
Original features
47
Production features
46
Production algorithm
XGBoost
Production ROC-AUC
0.6606
Decision threshold
0.15
SQL database
SQLite
API framework
FastAPI
Automated tests
3
Model version
careai_xgboost_v1
Monitoring
Prediction + drift monitoring
