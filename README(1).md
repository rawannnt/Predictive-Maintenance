# ⚙️ Smart Manufacturing — Predictive Maintenance

A Machine Learning project for predicting whether an industrial machine requires maintenance using sensor and machine-condition data.

## 🚀 Features

- 🔮 **Single Prediction** — Enter sensor readings and receive an instant maintenance prediction with probability.
- 📊 **Batch Prediction** — Upload a CSV file and predict maintenance requirements for multiple machines.
- 📈 **Feature Importance** — Visualize the most influential features.
- 📋 **Model Evaluation** — Accuracy, Precision, Recall, F1-score, ROC-AUC, confusion matrix, and ROC curves.
- 🛡️ **Leakage Analysis** — Potential target-leaking variables were investigated and excluded.
- ⏱️ **Chronological Split** — Data is split by time rather than randomly.

## 🧠 Machine Learning

### Problem Type

**Binary Classification**

- `0` → Maintenance not required
- `1` → Maintenance required

### Models Explored

- Logistic Regression
- Random Forest
- LightGBM
- Stacking Ensemble

The deployed application uses **LightGBM** based on its predictive performance and suitability for deployment.

### Training Strategy

- **Class imbalance:** `class_weight='balanced'`
- **Hyperparameter tuning:** `RandomizedSearchCV`
- **Cross-validation:** `TimeSeriesSplit`
- **Train/Test:** Chronological split
- **Training period:** First two months
- **Testing period:** Following/final period
- **No random shuffling** for the final time-based split

## 📌 Final Model Features

- `temperature`
- `vibration`
- `humidity`
- `pressure`
- `predicted_remaining_life`

### Leakage Prevention

The following variables were investigated as potential leakage sources and excluded from the final model:

- `machine_status`
- `failure_type`
- `anomaly_flag`
- `downtime_risk`

`timestamp` is used to preserve chronological order but is **not used as a model predictor**.

## 📊 Exploratory Data Analysis

The project includes:

- Dataset structure and data types
- Missing values and duplicates
- Descriptive statistics
- Histograms and distributions
- Skewness analysis
- Boxplots and outlier detection
- Sensor features vs. maintenance requirement
- Categorical features vs. maintenance requirement
- Target class distribution
- Correlation analysis
- Machine-level anomaly analysis
- Remaining-life analysis
- Time-series analysis
- Leakage investigation

## 📈 Evaluation

Models are evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix
- ROC Curves
- Precision-Recall analysis

## 🖥️ Streamlit Application

The application allows users to:

1. Enter sensor readings manually.
2. Receive a maintenance-required prediction.
3. View the predicted probability.
4. Upload a CSV for batch predictions.
5. View feature importance.

## 🛠️ Technologies

Python · Pandas · NumPy · Scikit-learn · LightGBM · Matplotlib · Seaborn · Streamlit · Joblib

## 📁 Project Structure

```text
├── app.py
├── train_model.py
├── requirements.txt
├── .streamlit/
│   └── config.toml
├── data/
│   └── smart_manufacturing_data.csv
├── model/
│   └── model.pkl
└── notebook/
    └── smart_manufacturing_final_organized.py
```

## ▶️ Run Locally

```bash
git clone https://github.com/<your-username>/predictive-maintenance-app.git
cd predictive-maintenance-app
pip install -r requirements.txt
python train_model.py
streamlit run app.py
```

## ☁️ Deploy on Streamlit Community Cloud

1. Push the repository to GitHub.
2. Open Streamlit Community Cloud.
3. Select **New App**.
4. Select this repository.
5. Set the main file to `app.py`.
6. Deploy.

## 🎯 Project Goal

Demonstrate how Machine Learning can be applied to **Smart Manufacturing and Industrial IoT** to predict maintenance requirements from machine sensor data and support proactive maintenance decisions.

## 🔄 ML Workflow

**EDA → Preprocessing → Leakage Detection → Feature Selection → Time-Based Split → Model Training → Evaluation → Deployment**
