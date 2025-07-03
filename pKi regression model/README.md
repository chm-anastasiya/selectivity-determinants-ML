pKi Regression Models 
==========================================

This directory contains a Jupyter notebook that **trains and analyses
binding-affinity (pKi) regression models** for six serotonin receptors
(5-HT1A, 5-HT2A, 5-HT2B, 5-HT5A, 5-HT6, 5-HT7).

Notebook
--------

1.**`pKi_regression_all_receptors.ipynb`**
* trains LightGBM regressors to predict pKi (–log₁₀ Ki);  
* uses ECFP4 fingerprints + RDKit descriptors;  
* saves R² / RMSE / MAE, feature rankings and
`model.pkl` files under results/<receptor>/.

Input
-----

Cleaned CSV files for each receptor in `Cleaned_data/`
(`cleaned_5HT1A.csv`, `cleaned_5HT2A.csv`, …) containing SMILES, Ki and
RDKit descriptors.

Output
------
results/<receptor>/
- LGBM_pKi_<receptor>.pkl       (fitted model)
- scaler_pKi_<receptor>.pkl     (StandardScaler for descriptors)
- metrics.json                  (R², RMSE, MAE (train / CV))


Quick start
-----------

1. Verify that the six `cleaned_5HT*.csv` files are present in `Cleaned_data/`.  
2. Run **`pKi_regression_all_receptors.ipynb`** to train the models.  
3. Trained models and metrics will appear in the `results/<receptor>/`
   folders.
   
These `.pkl` files are later loaded automatically by the **Selectivity model**
and **Prediction for new SMILES** notebooks.
