# Machine-Aided Self-diagnostic Prediction Models for Polycystic Ovary Syndrome (PCOS)

[![Kaggle](https://img.shields.io/badge/Kaggle-Ready-20BEFF?style=flat&logo=kaggle)](https://www.kaggle.com/)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Overview

This repository contains a comprehensive implementation of the PCOS prediction pipeline from the research paper **"Machine-Aided Self-diagnostic Prediction Models for Polycystic Ovary Syndrome: Observational Study"** published in *JMIR Formative Research* (2022).

The implementation includes both **Patient Models** (using only noninvasive measures) and **Provider Models** (using all available clinical data), along with subgroup analysis using PCA and k-means clustering.

## 🎯 Key Features

- **Patient Model**: Self-diagnosis using noninvasive measures (81-82.5% accuracy)
- **Provider Model**: Clinical diagnosis using all features (87.5-90.1% accuracy)
- **Subgroup Analysis**: PCA + K-means clustering for BMI-based patient stratification
- **Model Interpretability**: SHAP values for feature importance analysis
- **Comprehensive Visualizations**: 20+ professional plots for data exploration and results

## 📁 Repository Structure

```
.
├── pcos_prediction_pipeline.ipynb          # Main Kaggle-ready notebook
├── PCOS_data_without_infertility.xlsx      # Main dataset (541 samples, 44 features)
├── PCOS_infertility.csv                    # Supplementary infertility data
├── Machine-Aided Self-diagnostic Prediction Models for Polycystic Ovary Syndrome- Observational Study.pdf
└── README.md                                # This file
```

## 📊 Dataset

**Source**: 541 women's health records from 10 hospitals in Kerala, India

**Features Categories**:
- **Anthropomorphic Variables** (6): BMI, Height, Hip, Waist, Waist:Hip Ratio, Weight
- **Symptom Variables** (9): Skin darkening, Acne, Hair loss, Hair growth, Menstrual cycle, Weight gain, etc.
- **Given Variables** (5): Age, Blood Group, Marriage Status, Pregnancy, Abortions
- **Test Result Variables** (21): FSH, LH, TSH, AMH, PRL, Vitamin D3, Blood Pressure, Follicle counts, etc.

**Target Variable**: PCOS (Y/N) - Binary classification
- PCOS Positive: 170 cases (32.3%)
- PCOS Negative: 356 cases (67.7%)

## 🛠️ Methodology

### Models
- **Algorithm**: CatBoost (Gradient Boosting Decision Trees)
- **Parameters**: iterations=500, learning_rate=0.1, depth=6
- **Validation**: K-fold cross-validation
  - Full dataset: 5-fold CV × 3 iterations
  - Subgroups: 3-fold CV × 5 iterations

### Workflow
1. **Data Preprocessing**: Handle missing values, encode categorical variables
2. **Exploratory Data Analysis**: Compare PCOS+ vs PCOS- groups
3. **Feature Engineering**: Categorize features into noninvasive and invasive
4. **PCA Analysis**: Extract 5 principal components from anthropomorphic variables
5. **K-means Clustering**: Identify 2 BMI-based subgroups
6. **Model Training**: Train both Patient and Provider models
   - One-to-all models (entire dataset)
   - Subgroup-specific models
7. **Model Evaluation**: Accuracy, Sensitivity, Precision, F1-score
8. **Interpretability**: SHAP analysis for feature importance

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy scikit-learn catboost shap matplotlib seaborn openpyxl scipy
```

### Running the Notebook

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Farzine/Polycystic-ovary-syndrome--PCOS-.git
   cd Polycystic-ovary-syndrome--PCOS-
   ```

2. **Open the notebook**:
   ```bash
   jupyter notebook pcos_prediction_pipeline.ipynb
   ```

3. **Run all cells**: Execute cells sequentially or use "Run All"

### Using on Kaggle

1. Upload `pcos_prediction_pipeline.ipynb` to Kaggle
2. Add the datasets as input files:
   - `PCOS_data_without_infertility.xlsx`
   - `PCOS_infertility.csv`
3. Run the notebook

## 📈 Expected Results

### Patient Model (Noninvasive Features)
| Model | Accuracy | Sensitivity | Precision | F1-Score |
|-------|----------|-------------|-----------|----------|
| One-to-All | 0.825 | 0.851 | 0.900 | 0.874 |
| Subgroup 1 | 0.815 | 0.837 | 0.931 | 0.880 |
| Subgroup 2 | 0.810 | 0.827 | 0.870 | 0.846 |

### Provider Model (All Features)
| Model | Accuracy | Sensitivity | Precision | F1-Score |
|-------|----------|-------------|-----------|----------|
| One-to-All | 0.875-0.901 | High | High | High |
| Subgroup 1 | Similar | High | High | High |
| Subgroup 2 | Similar | High | High | High |

## 📊 Visualizations

The notebook includes:
- Target variable distribution plots
- Anthropomorphic and symptom variable comparisons
- Correlation heatmaps
- PCA biplots and scree plots
- K-means clustering visualizations
- Subgroup characteristic comparisons
- Model performance comparison charts
- SHAP summary plots, waterfall plots, and dependence plots
- Confusion matrices

## 🔍 Key Findings

1. **Most Important Noninvasive Features** (Patient Model):
   - Acanthosis nigricans (skin darkening)
   - Irregular menstrual cycle
   - Weight gain
   - BMI

2. **Most Important Clinical Features** (Provider Model):
   - AMH (Anti-Müllerian hormone)
   - Follicle counts (left and right ovaries)
   - FSH/LH ratio
   - Blood pressure

3. **Subgroup Differences**:
   - Subgroup 1: Lower BMI, better prediction accuracy
   - Subgroup 2: Higher BMI, more challenging predictions

## 📚 Citation

If you use this implementation, please cite the original paper:

```bibtex
@article{zigarelli2022machine,
  title={Machine-Aided Self-diagnostic Prediction Models for Polycystic Ovary Syndrome: Observational Study},
  author={Zigarelli, Angela and Jia, Ziyang and Lee, Hyunsun},
  journal={JMIR Formative Research},
  volume={6},
  number={3},
  pages={e29967},
  year={2022},
  publisher={JMIR Publications}
}
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 👥 Authors

- **Original Paper**: Angela Zigarelli, Ziyang Jia, Hyunsun Lee (UMass Amherst)
- **Implementation**: Farzine

## 🔗 Links

- [Original Paper](https://formative.jmir.org/2022/3/e29967)
- [Dataset Source](https://www.kaggle.com/datasets/prasoonkottarathil/polycystic-ovary-syndrome-pcos)
- [JMIR Formative Research](https://formative.jmir.org/)

## ⚠️ Disclaimer

This implementation is for research and educational purposes only. It should not be used as a substitute for professional medical advice, diagnosis, or treatment. Always consult with qualified healthcare providers for medical decisions.

## 📧 Contact

For questions or feedback, please open an issue on GitHub.

---

**Last Updated**: February 2026
