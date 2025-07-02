pKi Regression Models 
==========================================

This directory provides a Jupyter notebook that builds **regression models
to predict binding affinity (pKi)** for six serotonin receptors
(5-HT1A, 5-HT2A, 5-HT2B, 5-HT5A, 5-HT6, 5-HT7).

Notebook
--------

**`pKi_regression_all_receptors.ipynb`**

* trains LightGBM regressors to predict pKi (–log₁₀ Ki);  
* uses ECFP4 fingerprints + RDKit descriptors;  
* saves R² / RMSE / MAE, feature rankings and
`model.pkl` files under results/<receptor>/.

Input data
----------

Cleaned CSV files for each receptor in `Cleaned_data/`
(`cleaned_5HT1A.csv`, `cleaned_5HT2A.csv`, …) containing SMILES, Ki and
RDKit descriptors.

Output structure
----------------
results/<receptor>/

results/<receptor>/
- LGBM_pKi_<receptor>.pkl       # fitted model
- scaler_pKi_<receptor>.pkl     # StandardScaler for descriptors
- metrics.json                  # R², RMSE, MAE (train / CV)


Quick start
-----------

1. Make sure the six `cleaned_5HT*.csv` files are present in
   **`Cleaned_data/`**.  
2. Open **`pKi_regression_all_receptors.ipynb`** and run.  
3. Trained models and evaluation figures will appear in the `models/` sub-folder.

These `.pkl` files are later loaded automatically by the **Selectivity model**
and **Prediction for new SMILES** notebooks.
