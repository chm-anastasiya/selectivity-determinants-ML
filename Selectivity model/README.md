Selectivity Model
=================

This folder contains three Jupyter notebooks that identify ligands shared by all
receptors, build *selectivity* (ΔpKi) classifiers and visualise the
*chemical-space separation* of selective versus non-selective ligands.

Notebooks
---------

1. **`common_smiles.ipynb`**  
   Reads `ki_long.parquet`, finds SMILES present in every receptor dataset,
   and writes `ligands_for_inference.csv`.

2. **`selectivity_models.ipynb`**  
   For each receptor pair trains a LightGBM regressor on ΔpKi (meta‐features = pKi & P(active));  
   saves `meta_<R1>_vs_<R2>.pkl` and writes `meta_metrics_summary.csv` under `models/sel/`.

3. **`UMAP_selevcitvity.ipynb`**  
   Projects the combined ECFP4 + RDKit descriptor space with UMAP;  
   colours points by the receptor for which each ligand is most selective;  
   saves plots to `umap_plots/UMAP_<R1>_vs_<R2>.png`.

Input
-----

* **`pair_datasets/pair_<R1>_<R2>.csv`** (ΔpKi tables generated previously).
* **`ligands_for_inference.csv`** (common SMILES list produced by
  **`common_smiles.ipynb`**).
* Trained pKi and binary‐activity models (read from sibling folders).

Output
------
models/sel/
- meta_<R1>vs<R2>.pkl (15 LightGBM meta-models)
- meta_metrics_summary.csv (R² / MAE per pair)
umap_plots/
-  UMAP_selectivity_<…>.png

Quick start
-----------

1. Run **`common_smiles.ipynb`** to generate `ligands_for_inference.csv`.  
2. Run **`selectivity_models.ipynb`** to train and save meta‐models.  
3. Run **`UMAP_selevcitvity.ipynb`** to visualise selectivity clusters.

The `.pkl` files are later loaded automatically by the **Prediction for new SMILES** notebooks.
