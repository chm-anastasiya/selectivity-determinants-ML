# selectivity-determinants-ML
Machine-learning project for analysing ligand selectivity with ChEMBL data

## 5-HT Ligand Activity, Affinity and Selectivity Pipeline

This repository provides a notebook-based workflow that predicts  

* **binary activity**,  
* **binding affinity** (*p*Ki), and  
* **receptor selectivity** (Δ*p*Ki)  

for ligands across six serotonin receptors  
(5-HT1A, 5-HT2A, 5-HT2B, 5-HT5A, 5-HT6, 5-HT7).

---

## Folder structure

0. Cleaned_data/ (input CSV files per receptor)
1. Binary_activity_models/ (binary classifiers + UMAP visualisation)
2. pKi_regression_model/  (pKi regression models)
3. Selectivity_model/ (selectivity models + UMAP visualisation) 
4. Prediction_new_SMILES/ (unified inference for novel molecules)

| Folder                     | Main notebooks / scripts                                                              | Key outputs                                                                                       |
|----------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **0.Cleaned_data**         | –                                                                                     | `cleaned_5HT1A.csv` …  (SMILES, Ki, RDKit descriptors)                         |
| **1.Binary_activity_models** | `binary_activity_all_receptors.ipynb`<br>`UMAP_activity_classification_all_receptors.ipynb` | `models/ <models>/`<br>`model.pkl`, `scaler.pkl`, ROC & PR curves, top_featurees.csv<br>`figs/UMAP_<receptor>.png` |
| **2.pKi_regression_model**   | `pKi_regression_all_receptors.ipynb`                                                 | `/models/pKi/`<br>`LGBM_pKi_<receptor>.pkl`, `scaler_pKi_<receptor>.pkl`    `/results/`<br> `metrics.json`   |
| **3.Selectivity_model**      | `common_smiles.ipynb`<br>`selectivity_models.ipynb`<br>`UMAP_selevcitvity.ipynb`       | `models/sel/`<br>`meta_<R1>_vs_<R2>.pkl`, `meta_metrics_summary.csv`<br>`umap_plots/UMAP_<…>.png`  |
| **4.Prediction_new_SMILES**  | `prediction_P(active)_Ki_ΔpKi.ipynb`| `new_predicted_Ki.csv`<br>`new_predicted_Pactive.csv`<br>`new_predicted_selectivity.csv`          |

---

## Quick Workflow

1. **Data preparation**  
   Ensure `cleaned_5HT*.csv` are present in `Cleaned_data/`.
2. **Binary activity models**  
   Run both notebooks in `Binary_activity_models/`.
3. **pKi regression models**  
   Run the notebook in `pKi_regression_model/`.
4. **Selectivity analysis**  
   Execute notebooks in `Selectivity_model/` **in this order**:  
   1. `common_smiles`;
   2. `selectivity_models`;
   3. `UMAP_selevcitvity`.
5. **Inference on new SMILES**  
   Place your SMILES list in `Prediction_new_SMILES/input_smiles.csv` and run the inference notebook.

Each folder contains its own mini-README with notebook-level details.

---

## Environment

1. **Install Miniconda (or Anaconda)**  
   Download the installer from <https://docs.conda.io/en/latest/miniconda.html> and follow the setup guide.
   
3. **Clone this repository**  
    git clone https://github.com/chm-anastasiya/selectivity-determinants-ML.git
    cd selectivity-determinants-ML
     
4. **Create and activate the Conda environment**  
    conda env create -f environment.yml
    conda activate selectivity-ml
