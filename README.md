# LiIonConductivityGraphs

## Overview
This repository contains code and data related to the publication following publication:
Classification of (Dis)ordered Structures as Superionic Lithium Conductors (https://doi.org/10.26434/chemrxiv-2024-712r9) 

## Repository Structure

### Notebooks

- **Step_1_Step_1_Create_Ordered_Configurations.ipynb**:  
  Creates ordered configurations of structures from labelled database. 

- **Step_2_Clean_and_Featurize_Labelled_Data.ipynb**:  
  Cleans and processes labelled data, extracting relevant graph-based and atomistic features for further analysis and model training. 
  
- **Step_3_Cluster_and_Generate_Train_Val_Test_Splits.ipynb**:  
  Creates train, validation, and test splits for k-fold and leave-one-cluster-out (LOCO) CV. Uses UMAP dimensionality reduction and DBSCAN to generate clusters based on ElMD representation. 
  
- **Step_4_Generate_Controls.ipynb**:  
  Generates mean and shuffled control datasets to validate the model performance.

- **Step_4_Featurize_Unlabelled_Data.ipynb**:  
  Processes the unlabelled Inorganic Crystal Structure Database (ICSD) and Materials Project data, extracting the same features as the labelled dataset for later prediction.

- **Step_5_KFold_Validation.ipynb**:  
  Performs K-Fold cross-validation on the training/validation set to evaluate model-feature performance across different random splits.

- **Step_7_Leave_One_Cluster_Out_Cross_Validation_Analysis.ipynb**:  
  Analyzes results from LOCO CV and hyperparamter optimization to evaluate model-feature performance.

- **Step_8_Test_Validation.ipynb**:  
  Handles the final evaluation of the holdout test set with the optimized AtomSets model ensemble.

- **Step_9_Predict_on_Unlabelled_Data.ipynb**:  
  Applies the trained model ensemble to classify Li-containing materials in the ICSD and Materials Project.

### Scripts

- **`hpo_classification.py`**:  
  Performs hyperparameter optimization (HPO) for classification models predicting superionic conductivity in Li-containing materials.

- **`hpo_classification_training_top_configurations_repeated_runs.py`**:  
  Performs repeated runs of training using the top configurations identified from hyperparameter optimization (HPO) for classification of superionic materials.

- **`model_training.py`**:  
  Handles the training of AtomSets models for k-fold cross-validation. It supports the use of pre-trained models and various input feature types.

- **`data_analysis.py`**:  
  Analyzes the training results, calculates relevant metrics for model-feature comparison.

- **`data_featurization.py`**:  
  Handles data featurization, including loading structures from CIF files, simplifying structures, generating MEGNet-compatible graphs, and calculating atomistic features for use in machine learning models.

### Figures

- Relevant figures or plots generated by the notebooks or scripts in this directory.

### Data
The labelled database used in this repository and corresponding publication contains experimental ionic conductivity values paired with experimental crystal structures from the Inorganic Crystal Structure Database (ICSD). Crystallographic information files (CIFs) for ICSD structures are not supplied and so users must have access to relevant CIF files in the database to replicate the entirety of this work.
 
### maml (MAterials Machine Learning)

Modified version of the `maml` package ([https://github.com/materialsvirtuallab/maml](https://github.com/materialsvirtuallab/maml)) from the Materials Virtual Lab. Documentation for the original package can be found at [https://materialsvirtuallab.github.io/maml/](https://materialsvirtuallab.github.io/maml/). The AtomSets code herein is modified to include dropout layers and L2 kernel regularization.

```bibtex
@misc{maml,
  author = {Chen, Chi and Zuo, Yunxing, Ye, Weike, Ji, Qi and Ong, Shyue Ping},
  title = {{Maml - materials machine learning package}},
  year = {2020},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/materialsvirtuallab/maml}},
}
```

Reference to AtomSets work:
```bibtex
Chen, C.; Ong, S. P. AtomSets as a hierarchical transfer learning framework for small and large materials
datasets. Npj Comput. Mater. 2021, 7, 173. https://doi.org/10.1038/s41524-021-00639-w
```

### megnet (MatErials Graph Network)
 
  MEGNet package (https://github.com/materialsvirtuallab/megnet) from the Materials Virtual Lab.
  Reference to original MEGNet Work:
  ```bibtex
  Chen, C.; Ye, W.; Zuo, Y.; Zheng, C.; Ong, S. P. Graph Networks as a Universal Machine Learning Framework for Molecules and Crystals. Chem. Mater. 2019, 31 (9), 3564–3572. https://doi.org/10.1021/acs.chemmater.9b01294.
  ```
  