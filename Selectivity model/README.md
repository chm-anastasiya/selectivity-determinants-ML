Selectivity Model
=================

This folder contains three notebooks that identify ligands shared by all
receptors, build *selectivity* (ΔpKi) classifiers and visualise the
*chemical-space separation* of selective versus non-selective ligands.

Notebooks
---------

| # | Notebook | Role |
|---|----------|------|
| 1 | **`common_smiles.ipynb`** | Extracts the subset of SMILES present in every receptor dataset (reads `ki_long.parquet` produced earlier) and writes `ligands_for_inference.csv`. |
| 2 | **`selectivity_models.ipynb`** | For each of the 15 receptor pairs trains a LightGBM regressor that predicts ΔpKi using outputs of the activity and pKi models as meta-features. Models are saved to `models/sel/` and a summary table is written to `models/sel/meta_metrics_summary.csv`. |
| 3 | **`UMAP_selevcitvity.ipynb`** | Projects ligands into 2-D UMAP space (ECFP4 + RDKit descriptors) and colours by the receptor for which the ligand is predicted to be most selective. Plots are saved to `umap_plots/`. |

Input
-----

* **`pair_datasets/pair_<R1>_<R2>.csv`** – ΔpKi tables generated in the
  *15_build_pair_datasets* step.  
* **`ligands_for_inference.csv`** – common SMILES list produced by
  **`common_smiles.ipynb`**.  
* Trained pKi and binary‐activity models (read from sibling folders).

Output structure
----------------
models/sel/
- meta_<R1>vs<R2>.pkl # 15 LightGBM meta-models
- meta_metrics_summary.csv # R² / MAE per pair
umap_plots/
-  UMAP_selectivity_<…>.png # 2-D chemical-space maps

s to predict ligand preference
  (selective if |ΔpKi| ≥ 1);  
* saves metrics, confusion matrices, ROC curves, feature rankings and
  `model.pkl` files under `results/selectivity_models/`.

3. **`UMAP_selevcitvity.ipynb`**  
  projects ligands into 2-D with UMAP, coloured by most-selective receptor
  pair;
  plots are written to `figs/UMAP_selectivity/`.


Quick start
-----------

1. **`common_smiles.ipynb`** – generates the cross-receptor SMILES list.  
2. **`selectivity_models.ipynb`** – trains ΔpKi meta-models.  
3. **`UMAP_selevcitvity.ipynb`** – visualises selectivity clusters.

After these steps the folder `models/sel/` will contain ready-to-use
selectivity models that are consumed by the final *Prediction for new
SMILES* stage.
