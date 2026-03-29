# Diabetes Classification Model

## Abstract

This project presents a machine learning approach for binary classification of diabetes status using logistic regression. The model leverages a dataset of clinical and anthropometric measurements to predict patient diabetic status, achieving competitive performance metrics suitable for preliminary medical screening applications.

---

## 1. Introduction

Diabetes mellitus remains a significant public health concern globally, affecting hundreds of millions of individuals. Early detection through predictive modeling can facilitate timely clinical intervention and preventive care strategies. This project implements a logistic regression classifier trained on comprehensive medical measurements to distinguish between diabetic and non-diabetic individuals.

### Objectives
- Develop a predictive classifier for diabetes status based on clinical measurements
- Evaluate model performance using standard classification metrics
- Provide interpretable decision boundaries for clinical relevance

---

## 2. Dataset Description

### Data Source
The diabetes dataset comprises 768 patient records with 9 clinical and demographic features.

### Features

| Feature | Type | Description | Unit/Range |
|---------|------|-------------|-----------|
| **PatientID** | Categorical | Unique patient identifier | - |
| **Pregnancies** | Numerical | Number of pregnancies | Count |
| **PlasmaGlucose** | Numerical | Plasma glucose concentration (2-hour post glucose load) | mg/dL |
| **DiastolicBloodPressure** | Numerical | Diastolic blood pressure | mmHg |
| **TricepsThickness** | Numerical | Triceps skin fold thickness | mm |
| **SerumInsulin** | Numerical | 2-Hour serum insulin level | μU/mL |
| **BMI** | Numerical | Body Mass Index (weight in kg/(height in m)²) | kg/m² |
| **DiabetesPedigree** | Numerical | Diabetes pedigree function (genetic predisposition) | Score |
| **Age** | Numerical | Patient age | Years |

### Target Variable
- **Diabetic**: Binary classification (0 = Non-diabetic, 1 = Diabetic)

### Data Statistics
- **Total Samples**: 10,000 patients
- **Features**: 8 predictive attributes
- **Class Distribution**: Imbalanced (~33% diabetic, ~67% non-diabetic)

---

## 3. Methodology

### 3.1 Data Preprocessing
- **Train-Test Split**: 70% training, 30% testing (random_state=0)
- **Feature Scaling**: Raw values used without normalization
- **Missing Values**: No imputation applied; dataset contains no missing entries

### 3.2 Model Architecture
**Algorithm**: Logistic Regression (Linear Classification)

**Hyperparameters**:
- Regularization coefficient (C): 10.0 (1/0.1)
- Solver: liblinear (efficient for binary classification)
- Optimization: L2 penalty (Ridge regularization)

### 3.3 Evaluation Metrics
- **Accuracy**: Overall classification correctness
- **AUC-ROC**: Area Under the Receiver Operating Characteristic Curve
- **ROC Curve**: True Positive Rate vs. False Positive Rate analysis

---

## 4. Results

### Model Performance

| Metric | Value |
|--------|-------|
| **Accuracy** | 77.4% |
| **AUC-ROC** | 0.848 |

### Interpretation
- The model correctly classifies approximately 77.4% of test samples
- The AUC-ROC of 0.848 indicates strong discriminative ability between classes
- The ROC curve demonstrates good sensitivity-specificity trade-off

---

## 5. Installation & Usage

### Prerequisites
- Python 3.7+
- Jupyter Notebook or JupyterLab
- Required libraries: pandas, scikit-learn, matplotlib, numpy

### Setup
```bash
pip install pandas scikit-learn matplotlib numpy
```

### Running the Model
1. Open `Train_diabetes_classification_model.ipynb` in Jupyter
2. Execute cells sequentially:
   - Cell 0: Load dataset
   - Cell 1: Feature extraction
   - Cell 2: Train-test split
   - Cell 3: Model training
   - Cell 4: Accuracy evaluation
   - Cell 5: AUC calculation
   - Cell 6: ROC curve visualization

### Expected Output
```
Reading data...
Splitting data...
Training model...
Accuracy: 0.774
AUC: 0.8484392258321308
```

---

## 6. Project Structure

```
.
├── README.md                                    # Project documentation
├── Train_diabetes_classification_model.ipynb    # Main analysis notebook
└── diabetes.csv                                 # Dataset (768 × 10)
```

---

## 7. Key Findings

1. **Plasma Glucose** and **BMI** are likely strong predictors of diabetic status
2. **Logistic Regression** provides an effective baseline for this classification task
3. The model demonstrates acceptable clinical utility for preliminary screening
4. Class imbalance (33% positive cases) may influence threshold optimization

---

## 8. Limitations & Future Work

### Current Limitations
- Binary logistic regression may not capture non-linear relationships
- No feature engineering or interaction terms explored
- Class imbalance not addressed (no SMOTE, weighted classes, or threshold tuning)
- No cross-validation or hyperparameter optimization performed

### Recommended Improvements
- Implement cross-validation for robust performance estimation
- Explore ensemble methods (Random Forest, Gradient Boosting)
- Apply SMOTE for class imbalance mitigation
- Conduct feature importance analysis
- Perform hyperparameter grid search
- Validate on external datasets

---

## 9. Requirements

```
pandas>=1.0.0
scikit-learn>=0.22.0
matplotlib>=3.0.0
numpy>=1.18.0
jupyter>=1.0.0
```

---