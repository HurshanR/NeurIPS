# NeurIPS 2025 Open Polymer Prediction - Bronze Medal Solution

🏆 **Bronze Medal Winner** - A comprehensive machine learning solution for predicting polymer properties using molecular descriptors and ensemble methods.

## 🎯 Competition Overview

This repository contains my solution for the [NeurIPS 2025 Open Polymer Prediction Challenge](https://www.kaggle.com/competitions/neurips-open-polymer-prediction-2025), where the goal was to predict five key polymer properties from molecular SMILES representations:

- **Tg** (Glass Transition Temperature)
- **FFV** (Free Volume Fraction) 
- **Tc** (Critical Temperature)
- **Density** (Polymer Density)
- **Rg** (Radius of Gyration)

## 🚀 Key Innovations & Improvements

### 1. **Leak-Proof GroupKFold Cross-Validation**
- Implemented proper group-based cross-validation using canonical SMILES as groups
- Prevents data leakage by ensuring molecules with identical canonical SMILES stay within the same fold
- Robust handling of invalid SMILES with unique fallback identifiers

### 2. **Advanced Feature Engineering**
- **RDKit Molecular Descriptors**: 200+ chemical descriptors including molecular weight, LogP, TPSA, rotatable bonds
- **MACCS Keys**: 167-bit molecular fingerprints for structural similarity
- **Morgan Fingerprints**: 1024-bit circular fingerprints for detailed molecular representation
- **Graph-based Features**: NetworkX-based molecular graph properties

### 3. **Multi-Model Ensemble Architecture**
- **XGBoost**: Primary model with hyperparameter optimization for each target
- **LightGBM**: Secondary gradient boosting with different loss functions
- **CatBoost**: Categorical feature handling for molecular structures
- **Ridge Regression**: Linear baseline on molecular descriptors only
- **OOF-Calibrated Blending**: Learned optimal ensemble weights from out-of-fold predictions

### 4. **Robust Data Handling**
- **SMILES Canonicalization**: Consistent molecular representation using RDKit
- **External Data Integration**: Augmented training data with supplementary datasets
- **Invalid SMILES Handling**: Safe fallback mechanisms for malformed molecular representations
- **Data Augmentation**: Gaussian Mixture Model-based synthetic data generation

### 5. **Target-Specific Optimization**
- Individual hyperparameter tuning for each polymer property
- Specialized loss functions (Huber loss for outlier robustness)
- Quantile regression for uncertainty estimation
- Weighted MAE evaluation matching competition metrics

## 📊 Results

- **Final Rank**: Bronze Medal (197th of 2240 Teams)
- **Methodology**: GroupKFold CV with 5-fold cross-validation
- **Evaluation Metric**: Weighted Mean Absolute Error (wMAE)
- **Key Strength**: Leak-proof validation ensuring reliable performance estimates

## 🛠️ Technical Implementation

### Dependencies
```bash
pip install -r requirements.txt
```

### Key Libraries
- **RDKit**: Molecular descriptor calculation and SMILES processing
- **XGBoost**: Primary gradient boosting model
- **LightGBM**: Secondary gradient boosting model
- **CatBoost**: Categorical feature handling
- **scikit-learn**: Preprocessing, cross-validation, and linear models
- **pandas/numpy**: Data manipulation and numerical computing

### Model Architecture
```
Input: SMILES → Canonicalization → Feature Engineering
├── Molecular Descriptors (200+ features)
├── MACCS Keys (167 bits)
├── Morgan Fingerprints (1024 bits)
└── Graph Features

Training: GroupKFold CV (5 folds)
├── XGBoost (target-specific hyperparameters)
├── LightGBM (Huber loss, quantile regression)
├── CatBoost (categorical handling)
└── Ridge (descriptor-only linear model)

Ensemble: OOF-Calibrated Blending
└── Ridge regression on out-of-fold predictions
```

## 🔬 Methodology Highlights

### 1. **Group-Based Cross-Validation**
- Prevents overfitting by ensuring molecular groups don't leak between folds
- Uses canonical SMILES as group identifiers
- Handles edge cases with invalid molecular representations

### 2. **Feature Engineering Pipeline**
- **Molecular Descriptors**: Comprehensive set of chemical properties
- **Fingerprints**: Multiple molecular representation schemes
- **Graph Features**: Network-based molecular topology analysis
- **Safe Processing**: Robust handling of invalid SMILES

### 3. **Ensemble Strategy**
- **Diverse Models**: Different algorithms capture different patterns
- **OOF Calibration**: Blending weights learned from out-of-fold predictions
- **Target-Specific Tuning**: Individual optimization for each polymer property

### 4. **Data Augmentation**
- **External Datasets**: Integration of supplementary polymer data
- **Synthetic Generation**: GMM-based data augmentation
- **SMILES Cleaning**: Robust preprocessing pipeline

## 📁 Repository Structure

```
├── neurips.ipynb          # Main solution notebook
├── requirements.txt       # Python dependencies
├── .gitignore            # Git ignore rules
└── README.md             # This file
```

## 🚀 Usage

1. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Run the Solution**:
   ```bash
   jupyter notebook neurips.ipynb
   ```

3. **Key Sections**:
   - Data loading and preprocessing
   - Feature engineering pipeline
   - GroupKFold cross-validation
   - Multi-model training
   - Ensemble blending
   - Final predictions

## 🔍 Key Technical Insights

### 1. **Leak Prevention**
- Canonical SMILES grouping prevents data leakage
- Robust validation ensures reliable performance estimates
- Group-based splitting maintains molecular integrity

### 2. **Feature Robustness**
- Safe handling of invalid SMILES prevents crashes
- Multiple molecular representations capture different aspects
- Descriptor-fingerprint combination provides comprehensive coverage

### 3. **Ensemble Effectiveness**
- OOF calibration prevents overfitting in blending
- Diverse models capture different prediction patterns
- Target-specific tuning optimizes individual performance

## 🏆 Competition Learnings

1. **Data Leakage Prevention**: Proper group-based CV is crucial for reliable validation
2. **Feature Engineering**: Molecular descriptors + fingerprints provide comprehensive coverage
3. **Ensemble Diversity**: Different algorithms capture different molecular patterns
4. **Robust Preprocessing**: Safe handling of edge cases prevents silent failures
5. **Target-Specific Optimization**: Individual tuning for each property improves performance

## 📈 Performance Analysis

The solution achieved bronze medal status through:
- **Leak-proof validation** ensuring reliable performance estimates
- **Comprehensive feature engineering** capturing molecular diversity
- **Robust ensemble methods** combining multiple prediction approaches
- **Target-specific optimization** tailored to each polymer property

## 🤝 Contributing

This repository contains my competition solution. Feel free to:
- Use the code for educational purposes
- Build upon the methodology
- Suggest improvements or extensions

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- **NeurIPS 2025** for organizing the competition
- **RDKit** community for molecular informatics tools
- **Kaggle** community for data science resources
- **Competition participants** for shared insights and discussions

---

*This solution represents a comprehensive approach to polymer property prediction using modern machine learning techniques, with particular emphasis on preventing data leakage and building robust, generalizable models.*
