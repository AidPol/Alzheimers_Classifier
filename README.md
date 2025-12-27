# Classifying Alzheimer’s Disease Severity from EEG using Machine Learning

**How well can Logistic Regression and Random Forest classify Alzheimer’s Disease severity based on statistical EEG features?**

---

## Introduction and Objective

Alzheimer’s disease is a progressive neurodegenerative disorder that severely impacts memory, cognition, and daily functioning. Diagnosis and severity assessment are traditionally performed using clinical evaluation and neuroimaging, which are often expensive and not widely accessible. EEG, on the other hand, is a low-cost and non-invasive technique capable of capturing brain electrical activity and subtle neural changes associated with disease progression.

In this project, machine learning was applied to EEG signals in **Python** using **scikit-learn** to classify the severity level of Alzheimer’s disease, demonstrating how computational methods can inform clinical diagnostics.

### Project Objective

The objective of the project was to automatically classify Alzheimer’s severity into three stages:

- **Mild**
- **Moderate**
- **Severe**

This classification was based entirely on EEG-derived features. Specifically, the goals were to:

- Extract quantitative statistical features from raw EEG signals  
- Train machine-learning models to learn differences between disease stages  
- Evaluate model performance on unseen patient data  

Achieving this highlights the potential of EEG as an accessible diagnostic tool and supports early detection and disease monitoring.

---

## Dataset and Preprocessing

The dataset used in this project was obtained from Kaggle:  
🔗 https://www.kaggle.com/datasets/nigarmahmoudshafiq/nigar-eeg-alzheimers-dataset-v1

### Dataset Overview

- **Total samples:** 15,820,760  
- **EEG channels:** 40 (not all channels available in every recording)  
- **Data format:** Separate recording files per patient  
- **Preprocessing:**  
  - Bandpass filtering  
  - Notch filtering  
  - Artifact removal  

Based on the filename, a script automatically assigned each patient a disease severity label:

| Label | Severity |
|------|----------|
| 1 | Mild |
| 2 | Moderate |
| 3 | Severe |

The script also:
- Standardised column names  
- Filled missing channels with `NaN` values  
- Combined all patient files into a single master dataset  

---

## Feature Extraction

The EEG signals were segmented into **2-second windows**, resulting in over **60,000 windows**.

For each window and each EEG channel, the following **statistical features** were extracted:

- Mean signal amplitude  
- Standard deviation  
- Variance  
- Hjorth mobility  
- Hjorth complexity  

These features capture:
- Overall neural activity levels  
- Signal variability  
- Frequency characteristics  
- Temporal signal complexity  

Each window was additionally tagged with:
- Disease severity label  
- Participant identifier  

All windows were stored in a single consolidated dataframe.

---

## Data Preparation

Before training the models, the following preprocessing steps were applied:

- Median imputation for missing values  
- Train-test split:
  - **70% training**
  - **30% testing**
- Feature scaling  

After these steps, the dataset was ready for machine-learning classification.

---

## Machine Learning and Evaluation

Two supervised machine-learning models were implemented:

- **Logistic Regression**
- **Random Forest**

### Evaluation Metrics

Model performance was assessed using:

- Accuracy  
- Precision  
- Recall  
- F1-score  
- ROC-AUC  
- Confusion matrix visualisation  

Both models were trained on the training set and evaluated on unseen test data.

---

## Results and Conclusions

### Results

- **Logistic Regression Accuracy:** **93%**
- **Random Forest Accuracy:** **88%**

Feature-importance analysis revealed that certain EEG channels and statistical features were particularly discriminative for Alzheimer’s severity, indicating that EEG signals contain meaningful patterns correlated with disease progression.

### Conclusions

This project demonstrates that Alzheimer’s disease severity can be effectively classified using EEG data and machine-learning techniques. The high performance of relatively simple models suggests that EEG may serve as a reliable and accessible biomarker for automated diagnosis and disease staging.

### Future Work

Potential extensions of this work include:

- Incorporating deep-learning models  
- Using larger and more diverse datasets  
- Extracting frequency-domain and time–frequency features  
- Exploring subject-independent validation strategies  

---

*This project highlights the promise of combining EEG and machine learning to support clinical decision-making in neurodegenerative diseases.*
