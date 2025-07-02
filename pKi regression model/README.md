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
* saves R² / RMSE / MAE, scatter & residual plots, feature rankings and
`model.pkl` files under results/<receptor>/.

Input data
----------

Cleaned CSV files for each receptor  
(`cleaned_5HT1A.csv`, `cleaned_5HT2A.csv`, …) containing SMILES, Ki and
RDKit descriptors.

Output structure
----------------
results/<receptor>/

- true_vs_pred_scatter.png
- residuals_hist.png
- metrics.json # R2, RMSE, MAE
- feature_importances.csv
- model.pkl

Quick start
-----------

1. Open **`pKi_regression_all_receptors.ipynb`**.  
2. Set `CSV_DIR` to the folder with the cleaned CSV files.  
3. Run all cells to train the models and generate the results.

