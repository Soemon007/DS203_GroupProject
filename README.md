# Economic Development Classification Using HDI 
## DS203 Course Project | Classification Project

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge)

This project aims to classify countries into 3 self-engineered HDI levels based on World Bank indicators on the economy, healthcare, etc.
We compare a majority-class baseline, multinomial logistic regression, a decision tree and a random forest, with and without PCA. If these models can predict a country’s HDI tier, they can give an early estimate where the HDI is late or absent. 

Video explaining the report is in the ![google drive](https://drive.google.com/drive/folders/1qW_tXh5uZ62qnTF1OdtEX2YPX2sNgLer?usp=drive_link)

---

## Contributors

* Rehan Mallik (@Soemon007)
* Vedant Iyengar (@eclipse1299)
* Siddhartha Nair (@SynapticSaurian)

---

## Repository Structure

```text
├── code                      # This folder contains all the relevant jupyter notebooks
├── deliverables              # This folder contains the final report and data dictionary 
├── data                      # This folder contains the main sources of data, including the primary dataset
└── README.md
```
--- 

## Results

Models were trained on PCA features (components covering >=90% of variance) after median imputation, missingness indicators, and one-hot encoding. Following are the results:

### Validation (single stratified split)

| Model | Macro F1 |
| :--- | :---: |
| Majority Class Baseline | 0.22 |
| Multinomial Logistic Regression | 0.86 |
| Decision Tree | 0.72 |
| Random Forest | 0.84 |

### 5-fold Hyperparameter Tuning

| Model | Hyperparameter | Mean Macro F1 |
| :--- | :--- | :---: |
| Multinomial Logistic Regression | `C=1` | 0.801 |
| Decision Tree | `max_depth=3` | 0.708 |
| Random Forest | `n_estimators=200` | 0.759 |

### Test

| Model | Macro F1 |
| :--- | :---: |
| Multinomial Logistic Regression | 0.96 |
| Decision Tree | 0.90 |
| Random Forest | 0.93 |
 
### Takeaways / Observations
- Every model performs better than the baseline, implying that the signal suggested in the problem statement is real
- Logistic regression did the best on validation and testing. Its edge over the tree models suggests that maybe the features have a linear relationship with HDI and thus Logistic regression which assigns a weight to each feature and    assumes linearity is able to predict HDI better than tree models which make sharp decisions.
