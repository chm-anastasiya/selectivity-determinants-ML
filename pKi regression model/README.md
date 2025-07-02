# pKi regression models
pKi Regression Models (5-HT Receptor Panel)
==========================================

This directory provides a Jupyter notebook that builds **regression models
to predict binding affinity (pKi)** for six serotonin receptors
(5-HT1A, 5-HT2A, 5-HT2B, 5-HT5A, 5-HT6, 5-HT7).

Notebook
--------

**`pKi_regression_all_receptors.ipynb`**

* Features: ECFP4 fingerprints (radius = 2, 1024 bits) + RDKit descriptors  
* Target: pKi = –log₁₀(Ki [M])  
* Model: LightGBM regressor, 5-fold cross-validation, Optuna
  hyper-parameter search  
* Outputs per receptor: R², RMSE, MAE, scatter/residual plots,
  ranked feature list, `model.pkl`

Input data
----------

Cleaned CSV files for each receptor  
(`cleaned_5HT1A.csv`, `cleaned_5HT2A.csv`, …) containing SMILES, Ki and
RDKit descriptors.

Output structure
----------------


