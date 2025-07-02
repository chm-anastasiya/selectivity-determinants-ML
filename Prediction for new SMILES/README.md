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
* writes the combined results to **`predictions.csv`** and generates an
  annotated scatter / heat-map under **`results/prediction/`**.

Input
-----
* **`input_smiles.csv`** (or any CSV you pass): one column named `Smiles`  
  The example file shipped here is `5ht2c.csv`.
  

Output
------

| File | Description |
|------|-------------|
| `new_predicted_Ki.csv` | pKi → Ki (nM) predictions for every receptor |
| `new_predicted_Pactive.csv` | probability of activity for every receptor |
| `new_predicted_selectivity.csv` | ΔpKi matrix for all receptor pairs |

All files are saved in the current working directory.


Quick start
-----------

1. Place your SMILES in `input_smiles.csv`.  
2. Open **`prediction_P(active)_Ki_ΔpKi.ipynb`**, check the path to the
   trained models (defaults to `results/` from earlier steps).  
3. Run all cells.
