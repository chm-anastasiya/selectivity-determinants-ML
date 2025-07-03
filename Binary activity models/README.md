Binary Activity Models 
==========================================

This directory contains two Jupyter notebooks that **train and analyse binary (active / inactive) classification models** for six serotonin receptors (5-HT1A, 5-HT2A, 5-HT2B, 5-HT5A, 5-HT6, 5-HT7).

Notebooks
---------
1. **`binary_activity_all_receptors.ipynb`**
* trains LightGBM classifiers (active = Ki < 1000 nM);
* uses ECFP4 fingerprints + RDKit descriptors;
* saves metrics, curves, feature rankings and model.pkl files.

2. **`UMAP_activity_classification_all_receptors.ipynb`**
* projects the same feature space with UMAP;
* produces 2-D plots coloured by activity class;
* files are written to figs/UMAP_<receptor>.png.



Input
-----

Cleaned CSV files for each receptor in `Cleaned_data/`
(`cleaned_5HT1A.csv`, `cleaned_5HT2A.csv`, …) containing SMILES, Ki and
RDKit descriptors.

Output
------
Binary activity models/ models/
- LGBM_ECFP_RDKit_5HT1A.pkl
- scaler_5HT1A.pkl
-… # one pair per receptor
- metrics_summary.csv (ROC-AUC, F1, MCC, Precision, Recall)
  
results/
- oof_pred_<receptor>.npy (out-of-fold probabilities)
- y_<receptor>.npy (true labels for OOF)

results/<receptor>/
- roc_curve.png
- pr_curve.png
- confusion_matrix
- top_features.csv
- top_bits_fragments.html
  
figs/
- UMAP_<receptor>.png

Quick start
-----------

1. Verify that the six `cleaned_5HT*.csv` files are present in `Cleaned_data/`.   
2. Run **`binary_activity_all_receptors.ipynb`** to train the models.
3. Run **`UMAP_activity_classification_all_receptors.ipynb`** to create the UMAP plots.

   
These `.pkl` files are later loaded automatically by the **Selectivity model**
and **Prediction for new SMILES** notebooks.
