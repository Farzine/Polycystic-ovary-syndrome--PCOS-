# Quick Start Guide - PCOS Prediction Pipeline

## 🚀 Quick Start

### Option 1: Run Locally with Jupyter

```bash
# 1. Clone the repository
git clone https://github.com/Farzine/Polycystic-ovary-syndrome--PCOS-.git
cd Polycystic-ovary-syndrome--PCOS-

# 2. Install dependencies
pip install pandas numpy scikit-learn catboost shap matplotlib seaborn openpyxl scipy jupyter

# 3. Launch Jupyter
jupyter notebook pcos_prediction_pipeline.ipynb

# 4. Run all cells (Kernel > Restart & Run All)
```

### Option 2: Run on Kaggle

1. **Go to Kaggle**: https://www.kaggle.com/
2. **Create New Notebook**: Click "New Notebook"
3. **Upload Notebook**: 
   - File > Import Notebook
   - Select `pcos_prediction_pipeline.ipynb`
4. **Add Data**:
   - Click "Add Data" > "Upload"
   - Upload `PCOS_data_without_infertility.xlsx`
   - Upload `PCOS_infertility.csv`
5. **Run**: Click "Run All"

### Option 3: Run in Google Colab

```python
# 1. Upload notebook to Google Drive
# 2. Open with Google Colab
# 3. Upload data files when prompted
# 4. Run all cells
```

## 📊 What the Notebook Does

### Data Analysis (Sections 1-5)
- Loads 541 patient records
- Explores distributions and correlations
- Categorizes 41 features into 4 groups
- Handles missing values and encoding

### Subgroup Analysis (Sections 6-8)
- Applies PCA to extract 5 principal components
- Uses k-means to identify 2 BMI-based subgroups
- Compares subgroup characteristics

### Patient Model (Section 9)
- Trains models using only noninvasive features
- Reports accuracy ~81-82.5%
- Use case: Self-diagnosis without medical tests

### Provider Model (Section 10)
- Trains models using all available features
- Reports accuracy ~87.5-90.1%
- Use case: Clinical decision support

### Interpretability (Section 12)
- SHAP analysis shows which features matter most
- Visualizes feature importance
- Explains individual predictions

## 🎯 Expected Runtime

- **Full notebook**: 5-10 minutes (depending on hardware)
- **Key computations**:
  - Data loading: < 1 minute
  - PCA & clustering: < 1 minute
  - Model training (6 models): 2-5 minutes
  - SHAP analysis: 2-4 minutes

## 📈 Key Results to Look For

### Patient Model Performance
- **Accuracy**: 0.810 - 0.825
- **Sensitivity**: 0.827 - 0.851
- **Precision**: 0.870 - 0.931
- **F1-score**: 0.846 - 0.880

### Provider Model Performance
- **Accuracy**: 0.875 - 0.901
- **Sensitivity**: High (>0.85)
- **Precision**: High (>0.85)
- **F1-score**: High (>0.85)

### Top Features (Patient Model)
1. Skin darkening (acanthosis nigricans)
2. Irregular menstrual cycle
3. Weight gain
4. BMI

### Top Features (Provider Model)
1. AMH (Anti-Müllerian hormone)
2. Follicle counts
3. FSH/LH ratio
4. Blood pressure

## 🔧 Troubleshooting

### Issue: Module not found
```bash
pip install <module_name>
```

### Issue: Data file not found
- Ensure data files are in the same directory as the notebook
- On Kaggle: Add files using "Add Data"
- On Colab: Upload files when prompted

### Issue: Out of memory
- Reduce number of CV iterations in the code
- Use a smaller subset of data for testing

### Issue: CatBoost takes too long
- Reduce `iterations` parameter (e.g., from 500 to 100)
- Increase `learning_rate` (e.g., from 0.1 to 0.3)

## 📝 Customization

### Change Cross-Validation Settings
```python
# In the cross_validate_catboost function
n_splits=5,  # Change to 3 for faster execution
n_iterations=3  # Change to 1 for faster execution
```

### Change CatBoost Parameters
```python
model = CatBoostClassifier(
    iterations=500,  # Reduce for faster training
    learning_rate=0.1,  # Increase for faster convergence
    depth=6,  # Reduce for simpler model
    random_seed=42
)
```

### Add More Visualizations
- Section 3 (EDA): Add your own plots
- Section 12 (SHAP): Explore different SHAP plots

## 🆘 Getting Help

- **Issues**: Open an issue on GitHub
- **Questions**: Check the README.md
- **Paper**: Read the original research paper (included in repo)

## ✅ Validation Checklist

After running the notebook, verify:
- [ ] All cells executed without errors
- [ ] 20+ visualizations generated
- [ ] 6 models trained (3 Patient + 3 Provider)
- [ ] Performance metrics displayed
- [ ] SHAP plots generated
- [ ] Accuracy matches expected ranges

## 🎓 Learning Objectives

By the end of this notebook, you will understand:
- How to preprocess medical data
- How to apply PCA for dimensionality reduction
- How to use k-means for patient stratification
- How to train and evaluate CatBoost models
- How to interpret ML models with SHAP
- How to compare model performance across subgroups

## 📚 Further Reading

- [CatBoost Documentation](https://catboost.ai/)
- [SHAP Documentation](https://shap.readthedocs.io/)
- [Original Paper](https://formative.jmir.org/2022/3/e29967)
- [PCOS Information](https://www.who.int/news-room/fact-sheets/detail/polycystic-ovary-syndrome)

---

**Happy Learning! 🎉**
