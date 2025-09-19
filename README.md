# NeurIPS 2025 Open Polymer Prediction - Data Leakage Fix

🔧 **Data Leakage Solution** - Fixed critical data leakage issues in polymer property prediction by implementing proper GroupKFold cross-validation.

## 🎯 Competition Overview

This repository contains my contribution to the [NeurIPS 2025 Open Polymer Prediction Challenge](https://www.kaggle.com/competitions/neurips-open-polymer-prediction-2025), where the goal was to predict five key polymer properties from molecular SMILES representations:

- **Tg** (Glass Transition Temperature)
- **FFV** (Free Volume Fraction) 
- **Tc** (Critical Temperature)
- **Density** (Polymer Density)
- **Rg** (Radius of Gyration)

## 🚀 My Key Contribution

### **Leak-Proof GroupKFold Cross-Validation** ⭐ **MAIN CONTRIBUTION**
- **Fixed critical data leakage issue** in the original community approach
- Implemented proper group-based cross-validation using canonical SMILES as groups
- Prevents data leakage by ensuring molecules with identical canonical SMILES stay within the same fold
- Robust handling of invalid SMILES with unique fallback identifiers
- **This was the key innovation that enabled reliable validation**

### **Robust Data Handling**
- **SMILES Canonicalization**: Consistent molecular representation using RDKit
- **Invalid SMILES Handling**: Safe fallback mechanisms for malformed molecular representations
- **Group Integrity**: Ensures proper molecular grouping for leak-proof validation

## 🤝 Community Contributions Used

The modeling approach builds entirely on community work:

### **Community Model Integration**
- **XGBoost**: Community-optimized hyperparameters for each target
- **LightGBM**: Community secondary gradient boosting model
- **CatBoost**: Community categorical feature handling for molecular structures
- **Ridge Regression**: Community linear baseline on molecular descriptors
- **OOF-Calibrated Blending**: Community ensemble weight learning from out-of-fold predictions

### **Community Feature Engineering**
- **RDKit Molecular Descriptors**: 200+ chemical descriptors (community approach)
- **MACCS Keys**: 167-bit molecular fingerprints for structural similarity (community)
- **Morgan Fingerprints**: 1024-bit circular fingerprints (community)
- **Graph-based Features**: NetworkX-based molecular graph properties (community)

## 📊 Results

- **Final Rank**: Bronze Medal 🥉 (using community models + my leak fix)
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
- **XGBoost**: Community primary gradient boosting model
- **LightGBM**: Community secondary gradient boosting model
- **CatBoost**: Community categorical feature handling
- **scikit-learn**: Preprocessing, cross-validation, and linear models
- **pandas/numpy**: Data manipulation and numerical computing

### Model Architecture
```
Input: SMILES → Canonicalization → Feature Engineering (Community)
├── Molecular Descriptors (200+ features) - Community approach
├── MACCS Keys (167 bits) - Community approach
├── Morgan Fingerprints (1024 bits) - Community approach
└── Graph Features - Community approach

Training: FIXED GroupKFold CV (5 folds) ⭐ MY CONTRIBUTION
├── XGBoost (community hyperparameters)
├── LightGBM (community configuration)
├── CatBoost (community setup)
└── Ridge (community approach)

Ensemble: OOF-Calibrated Blending - Community method
└── Ridge regression on out-of-fold predictions
```

## 🔬 Methodology Highlights

### 1. **Group-Based Cross-Validation** ⭐ **MY MAIN INNOVATION**
- **Fixed critical data leakage** in original community approach
- Prevents overfitting by ensuring molecular groups don't leak between folds
- Uses canonical SMILES as group identifiers
- Handles edge cases with invalid molecular representations
- **This was the key differentiator that enabled reliable validation**

### 2. **Community Model Integration** (Not My Work)
- **XGBoost**: Community-optimized hyperparameters
- **LightGBM**: Community configuration
- **CatBoost**: Community setup
- **Ridge**: Community linear baseline

### 3. **Community Feature Engineering** (Not My Work)
- **Molecular Descriptors**: Community approach to chemical properties
- **Fingerprints**: Community molecular representation schemes
- **Graph Features**: Community network-based analysis
- **Safe Processing**: Community robust handling of invalid SMILES

### 4. **Community Ensemble Strategy** (Not My Work)
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
- **My leak-proof GroupKFold validation** - the key innovation that fixed data leakage
- **Community model integration** - building on proven approaches (not my work)
- **My robust group handling** - ensuring molecular integrity across folds
- **Reliable performance estimates** - confidence in model generalization enabled by my fix

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

*This solution demonstrates the critical importance of proper cross-validation in machine learning competitions. While the modeling approach builds entirely on community work, the key contribution was identifying and fixing a critical data leakage issue through proper GroupKFold implementation, which enabled reliable validation and ultimately led to the bronze medal performance.*
