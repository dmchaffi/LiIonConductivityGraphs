# LiIonConductivityGraphs

## Overview
This repository contains code and data related to classifying (Dis)ordered Structures as Superionic Lithium Conductors.

## Repository Structure

### Notebooks

- **Step_1_Clean_and_Featurize_Labelled_Data.ipynb**:  
  Cleans and processes labelled data, extracting relevant graph-based and atomistic features for further analysis and model training. 
  
- **Step_2_Cluster_and_Generate_Train_Val_Test_Splits.ipynb**:  
  Creates train, validation, and test splits for k-fold and leave-one-cluster-out (LOCO) CV. Uses UMAP dimensionality reduction and DBSCAN to generate clusters based on ElMD representation. 
  
- **Step_3_Generate_Controls.ipynb**:  
  Generates mean and shuffled control datasets to validate the model performance.

- **Step_4_Featurize_Unlabelled_Data.ipynb**:  
  Processes the unlabelled Inorganic Crystal Structure Database (ICSD) and Materials Project data, extracting the same features as the labelled dataset for later prediction.

- **Step_5_KFold_Validation.ipynb**:  
  Performs K-Fold cross-validation on the training/validation set to evaluate model-feature performance across different random splits.

- **Step_7_Leave_One_Cluster_Out_Cross_Validation_Analysis.ipynb**:  
  Analyzes results from LOCO CV to evaluate model-feature performance.

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

- **Labelled Data**:  
  Preprocessed data containing labeled materials with known ionic conductivity values.

- **Unlabelled Data**:  
  Raw data for materials without labeled ionic conductivity, which is used for predictions.

### MAML (MAterials Machine Learning)
 
  Modified version of the maml package (https://github.com/materialsvirtuallab/maml) from the Materials Virtual Lab. Documentation for the original package can be found at https://materialsvirtuallab.github.io/maml/. 
