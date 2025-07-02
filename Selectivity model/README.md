Selectivity Models 
==========================================

This directory contains three notebooks that compute ligand selectivity
(ΔpKi) between serotonin-receptor pairs and build machine-learning models
to predict receptor preference.

Notebooks
---------

1. **`common_smiles.ipynb`**  
* collects and canonicalises SMILES across all receptors;  
* outputs `common_smiles.csv` for downstream processing.

2. **`selectivity_models.ipynb`**  
* trains LightGBM classifiers to predict ligand preference
  (selective if |ΔpKi| ≥ 1);  
* saves metrics, confusion matrices, ROC curves, feature rankings and
  `model.pkl` files under `results/selectivity_models/`.

3. **`UMAP_selevcitvity.ipynb`**  
  projects ligands into 2-D with UMAP, coloured by most-selective receptor
  pair;
  plots are written to `figs/UMAP_selectivity/`.


Input data
----------

* `common_smiles.csv` and the per-receptor pKi prediction tables generated
  in the regression step (`results/<receptor>/pki_predictions.csv`).

Output structure
----------------

results/selectivity/
├── delta_pKi_matrix.csv
├── top_selective_ligands.csv
├── selectivity_heatmap.png
└── ΔpKi_histograms/

results/selectivity_models/
* <pair>_confusion_matrix.png
* <pair>_roc_curve.png
* <pair>_metrics.json
* <pair>_top_features.csv
* <pair>_model.pkl
