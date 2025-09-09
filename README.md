# Keratoconus Machine Learning Analysis

A comprehensive machine learning project for keratoconus detection and analysis using Pentacam corneal topography data and clinical information.

## Overview

This project focuses on developing machine learning models to detect and analyze keratoconus, a progressive eye disorder that causes the cornea to thin and bulge into a cone shape. The analysis combines Pentacam corneal topography measurements with clinical data including Cross-Linking (CXL) treatment information and keratoplasty procedures.

## Dataset

The project utilizes a rich dataset containing:

- **Pentacam Data**: Corneal topography measurements from 2,625 patients with 11,760 total scans
- **Clinical Data**: CXL treatment records and keratoplasty procedures
- **Patient Demographics**: Age, gender, and examination dates
- **Corneal Parameters**: 70+ Pentacam-derived features including:
  - Pachymetry measurements (corneal thickness)
  - Keratometry values (K1, K2, KMax)
  - Corneal volume measurements
  - Astigmatism indices
  - Corneal irregularity metrics


## Key Features

### Data Processing Pipeline
- **Patient ID Canonicalization**: Standardizes patient identifiers across datasets
- **Temporal Labeling**: Labels Pentacam scans based on treatment dates (CXL/keratoplasty)
- **Data Integration**: Combines Pentacam measurements with clinical treatment records
- **Quality Control**: Filters scans based on measurement quality and completeness

### Machine Learning Models
The project implements multiple machine learning algorithms:

- **Gradient Boosting Decision Trees (BDT)**
- **XGBoost**
- **Random Forest**
- **Support Vector Machines (SVM)**
- **Logistic Regression**

### Feature Engineering
- **Corneal Topography Features**: 70+ Pentacam-derived parameters
- **Temporal Features**: Age at examination, time since diagnosis
- **Clinical Features**: Treatment history and eye-specific information

### Evaluation Metrics
- **Accuracy, Precision, Recall, F1-Score**
- **ROC-AUC and Precision-Recall curves**
- **Confusion matrices**
- **Cohen's Kappa coefficient**

## Data Sources

1. **Pentacam Raw Data**: Corneal topography measurements from Oculus Pentacam
2. **CXL Treatment Data**: Cross-linking procedure records
3. **Clinical Diagnosis Data**: Keratoconus diagnosis and treatment history
4. **Demographic Data**: Patient age, gender, and examination details

## Methodology

### Labeling Strategy
- **Positive Class (y=1)**: Pentacam scans taken before CXL or keratoplasty procedures
- **Negative Class (y=0)**: Pentacam scans from patients who never underwent treatment

### Data Splitting
- Temporal-based splitting to ensure realistic clinical scenarios
- Cross-validation with proper patient-level separation

### Class Imbalance Handling
- **SMOTE (Synthetic Minority Oversampling Technique)**
- **ADASYN (Adaptive Synthetic Sampling)**
- **KMeansSMOTE**
- **SVMSMOTE**

## Results

The project generates comprehensive visualizations and performance metrics:

- **Confusion Matrices**: Model performance visualization
- **ROC Curves**: Sensitivity vs specificity analysis
- **Precision-Recall Curves**: Performance across different thresholds
- **Feature Importance**: Identification of most predictive corneal parameters
- **Temporal Analysis**: Performance over different time periods

## Usage

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn xgboost imbalanced-learn
```

### Running the Analysis
1. **Data Processing**: Execute `KeratoconusDataProcessing.ipynb` to preprocess raw data
2. **Model Training**: Run `KeratoconusAlgo.ipynb` to train and evaluate models
3. **Results**: View generated figures in `Paper_figs/` and `Results/` directories

### Key Notebooks
- `KeratoconusDataProcessing.ipynb`: Complete data preprocessing pipeline
- `KeratoconusAlgo.ipynb`: Machine learning model development and evaluation

## Clinical Significance

This project addresses the critical need for:
- **Early Detection**: Identifying keratoconus before significant vision loss
- **Treatment Planning**: Optimizing CXL and keratoplasty timing
- **Risk Stratification**: Assessing disease progression risk
- **Clinical Decision Support**: Providing objective diagnostic tools

## Technical Highlights

- **Large Dataset**: 2,625 patients with 11,760 Pentacam scans
- **Comprehensive Features**: 70+ corneal topography parameters
- **Temporal Analysis**: Time-series consideration for treatment planning
- **Robust Validation**: Patient-level cross-validation
- **Clinical Integration**: Real-world treatment data integration

## Research Publication

This work has been published in a peer-reviewed journal. Below is the abstract from our published research:

### Abstract

**Purpose:** The purpose of this study was to identify early indicators of keratoconus progression in Pentacam data using machine learning (ML) techniques.

**Methods:** A retrospective Pentacam tabular data set was created by retrieving 11,760 tomography tests performed in patients with keratoconus. Data for eyes labeled unstable based on their referral for cross-linking were differentiated from data for eyes labeled stable and not referred for follow-up procedures. A boosted decision tree was trained on the final data set using a cross-validation method.

**Results:** The final labeled data set included 1218 tomography tests. Training a ML model on a single test for each eye did not accurately predict disease progression, as indicated by the mean receiver-operating characteristic area under the curve of 0.59 ± 0.1, with precision of 0.27, recall of 0.3, and F1 score of 0.28. Training on serial tests for each eye included 819 tomography scans and yielded good prognostic abilities: a receiver-operating characteristic area under the curve of 0.75 ± 0.07, precision of 0.32, recall of 0.67, and F1 score of 0.43. In addition, 4 of the 55 Pentacam raw data parameters predominantly used the algorithm decision: age, central keratoconus index, Rs B, and D10 mm pachy.

**Conclusions:** This study revealed specific dominant parameters attributing to the classification of stability, which are not routinely assessed in determining progression in common practice. Using ML techniques, keratoconus deterioration was evaluated algorithmically with training on multiple tests, yet was not predicted by a single tomography test. Hence, our study highlights novel factors to the current consideration of cross-linking referral and may serve as a supportive tool for clinicians.

### Key Research Findings

- **Serial Testing Importance**: Single Pentacam tests showed limited predictive value (AUC: 0.59), while serial testing significantly improved performance (AUC: 0.75)
- **Critical Parameters**: Four key Pentacam parameters emerged as most predictive:
  - Patient age
  - Central keratoconus index (CKI)
  - Rs B (posterior corneal radius)
  - D10 mm pachymetry
- **Clinical Impact**: The model identified novel parameters not routinely used in clinical progression assessment
- **Practical Application**: Provides algorithmic support for cross-linking referral decisions

## Future Directions

- Integration of additional imaging modalities
- Longitudinal progression modeling
- Real-time clinical decision support systems
- Multi-center validation studies
- Implementation of serial testing protocols in clinical practice

## Contact

For questions about this analysis or collaboration opportunities, please refer to the project documentation or contact the research team.

---

*This project represents a comprehensive approach to keratoconus detection using machine learning and corneal topography data, with potential applications in clinical ophthalmology and automated screening systems. The research has been peer-reviewed and published, demonstrating the clinical validity and scientific rigor of the methodology.*