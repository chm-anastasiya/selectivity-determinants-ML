Prediction for New SMILES
===================================

This directory contains a Jupyter notebook that **applies all trained
models: binary activity classifiers, pKi regressors and pair-wise
selectivity classifiers** to unseen molecules provided as SMILES strings.

Notebook
--------

**`prediction_P(active)_Ki_ΔpKi.ipynb`**  
* loads the fitted models from previous steps;  
* featurises an input list of SMILES (ECFP4 + RDKit descriptors);  
* for each receptor predicts  
  * **P(active)** (probability of activity),  
  * **pKi** value;  
* for every receptor pair computes **ΔpKi** and the predicted
  selectivity class;

Input
-----

* **`input_smiles.csv`** — one-column CSV with a header `Smiles` (example: `5ht2c.csv`).  
  You may replace this file or edit the path in the first cell (notebook) or top of the script.

Output
------

new_predicted_Ki.csv (converts predicted pKi to Ki (nM) for each receptor)
new_predicted_Pactive.csv (P(active) for each receptor)
new_predicted_selectivity.csv (ΔpKi matrix and predicted selectivity class for all receptor pairs)

All files are saved in the current working directory.

Quick start
-----------

1. Place your SMILES in `input_smiles.csv`.  
2. Run a **`prediction_P(active)_Ki_ΔpKi.ipynb`**
