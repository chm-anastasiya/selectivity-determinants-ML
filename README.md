# Selectivity-Determinants-ML
Machine-learning project for analysing ligand selectivity using ChEMBL data

=======================================================

This repository contains a complete, notebook-based workflow for predicting
- *binary activity*,
- *binding affinity (pKi)* and
- *receptor selectivity (ΔpKi)*

of ligands across six serotonin receptors
(5-HT1A, 5-HT2A, 5-HT2B, 5-HT5A, 5-HT6, 5-HT7).

Folder Structure
----------------
0. Cleaned_data/ (input CSV files per receptor)
1. Binary_activity_models/ (binary classifiers + UMAP visualisation)
2. pKi_regression_model/  (pKi regression models)
3. Selectivity_model/ (selectivity ML, UMAP) 
4. Prediction_new_SMILES/ (unified inference for novel molecules)


| Folder | Main Notebooks | Key Outputs |
|--------|----------------|-------------|
| **0_Cleaned_data** | – | `cleaned_5HT*.csv` |
| **1_Binary_activity_models** | `binary_activity_all_receptors.ipynb`<br>`UMAP_activity_classification_all_receptors.ipynb` | `results/<receptor>/` ROC/PR curves, feature lists, `model.pkl`<br>`figs/UMAP_<receptor>.png` |
| **2_pKi_regression_model** | `pKi_regression_all_receptors.ipynb` | `results/<receptor>/` R² / RMSE / MAE, scatter & residual plots, `model.pkl` |
| **3_Selectivity_model** | `common_smiles.ipynb`<br>`selectivity_models.ipynb`<br>`UMAP_selevcitvity.ipynb` | `results/selectivity_models/` pair-wise classifiers<br>`figs/UMAP_selectivity/` selectivity clusters |
| **4_Prediction_new_SMILES** | `prediction_P(active)_Ki_ΔpKi.ipynb` | `results/prediction/predictions.csv` (P(active), *p*Ki, Δ*p*Ki)<br>`prediction_overview.png` |


---

## Quick Workflow

1. **Data preparation**  
   Ensure `cleaned_5HT*.csv` are present in `0_Cleaned_data/`.
2. **Binary activity models**  
   Run both notebooks in `1_Binary_activity_models/`.
3. **pKi regression models**  
   Run the notebook in `2_pKi_regression_model/`.
4. **Selectivity analysis**  
   Execute notebooks in `3_Selectivity_model/` **in this order**:  
   1. `common_smiles`;
   2. `selectivity_models`;
   3. `UMAP_selevcitvity`.
5. **Inference on new SMILES**  
   Place your SMILES list in `4_Prediction_new_SMILES/input_smiles.csv` and run the inference notebook.

Each folder contains a local README with concise, notebook-level instructions.

---

## Environment

- Python 3.10+ with the following packages:

- rdkit, lightgbm, scikit-learn, optuna, pandas, 
  numpy, tqdm, umap-learn, matplotlib, shape.

pip install -r requirements.txt
