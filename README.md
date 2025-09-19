# NeurIPS 2025 Open Polymer Prediction - Bronze Medal Solution

🏆 **Bronze Medal Winner** - A robust GroupKFold implementation that fixes data leakage issues in polymer property prediction using community models.

## 🎯 Competition Overview

This repository contains my solution for the [NeurIPS 2025 Open Polymer Prediction Challenge](https://www.kaggle.com/competitions/neurips-open-polymer-prediction-2025), where the goal was to predict five key polymer properties from molecular SMILES representations:

- **Tg** (Glass Transition Temperature)
- **FFV** (Free Volume Fraction) 
- **Tc** (Critical Temperature)
- **Density** (Polymer Density)
- **Rg** (Radius of Gyration)

## 🚀 Key Contributions & Improvements

### 1. **Leak-Proof GroupKFold Cross-Validation** ⭐ **MAIN CONTRIBUTION**
- **Fixed critical data leakage issue** in the original community approach
- Implemented proper group-based cross-validation using canonical SMILES as groups
- Prevents data leakage by ensuring molecules with identical canonical SMILES stay within the same fold
- Robust handling of invalid SMILES with unique fallback identifiers
- **This was the key innovation that led to bronze medal performance**

### 2. **Robust Data Handling**
- **SMILES Canonicalization**: Consistent molecular representation using RDKit
- **Invalid SMILES Handling**: Safe fallback mechanisms for malformed molecular representations
- **Group Integrity**: Ensures proper molecular grouping for leak-proof validation

### 3. **Community Model Integration**
- **XGBoost**: Used community-optimized hyperparameters for each target
- **LightGBM**: Integrated secondary gradient boosting model
- **CatBoost**: Added categorical feature handling for molecular structures
- **Ridge Regression**: Linear baseline on molecular descriptors
- **OOF-Calibrated Blending**: Learned optimal ensemble weights from out-of-fold predictions

### 4. **Feature Engineering** (Based on Community Approaches)
- **RDKit Molecular Descriptors**: 200+ chemical descriptors
- **MACCS Keys**: 167-bit molecular fingerprints for structural similarity
- **Morgan Fingerprints**: 1024-bit circular fingerprints
- **Graph-based Features**: NetworkX-based molecular graph properties

## 📊 Results

- **Final Rank**: Bronze Medal 🥉
- **Key Innovation**: Fixed GroupKFold data leakage issue
- **Methodology**: Leak-proof GroupKFold CV with 5-fold cross-validation
- **Evaluation Metric**: Weighted Mean Absolute Error (wMAE)
- **Main Contribution**: Proper group-based validation preventing overfitting

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
├── Molecular Descriptors (200+ features) - Community approach
├── MACCS Keys (167 bits) - Community approach
├── Morgan Fingerprints (1024 bits) - Community approach
└── Graph Features - Community approach

Training: FIXED GroupKFold CV (5 folds) ⭐ KEY CONTRIBUTION
├── XGBoost (community hyperparameters)
├── LightGBM (community configuration)
├── CatBoost (community setup)
└── Ridge (community approach)

Ensemble: OOF-Calibrated Blending - Community method
└── Ridge regression on out-of-fold predictions
```

## 🔬 Methodology Highlights

### 1. **Group-Based Cross-Validation** ⭐ **MAIN INNOVATION**
- **Fixed critical data leakage** in original community approach
- Prevents overfitting by ensuring molecular groups don't leak between folds
- Uses canonical SMILES as group identifiers
- Handles edge cases with invalid molecular representations
- **This was the key differentiator that led to bronze medal**

### 2. **Community Model Integration**
- **XGBoost**: Used community-optimized hyperparameters
- **LightGBM**: Integrated community configuration
- **CatBoost**: Applied community setup
- **Ridge**: Linear baseline from community approach

### 3. **Feature Engineering** (Community Methods)
- **Molecular Descriptors**: Community approach to chemical properties
- **Fingerprints**: Community molecular representation schemes
- **Graph Features**: Community network-based analysis
- **Safe Processing**: Robust handling of invalid SMILES

### 4. **Ensemble Strategy** (Community Approach)
- **Diverse Models**: Community ensemble of different algorithms
- **OOF Calibration**: Community blending weight learning
- **Target-Specific Tuning**: Community hyperparameter optimization

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

1. **Data Leakage Prevention**: **The most critical issue** - proper group-based CV is essential for reliable validation
2. **Community Model Integration**: Building on proven approaches can be very effective
3. **Group Integrity**: Ensuring molecular groups stay within folds prevents overfitting
4. **Robust Preprocessing**: Safe handling of edge cases prevents silent failures
5. **Validation Reliability**: Leak-proof validation gives confidence in model performance

## 📈 Performance Analysis

The solution achieved bronze medal status through:
- **Leak-proof GroupKFold validation** - the key innovation that fixed data leakage
- **Community model integration** - building on proven approaches
- **Robust group handling** - ensuring molecular integrity across folds
- **Reliable performance estimates** - confidence in model generalization

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
