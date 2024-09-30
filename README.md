# LiIonConductivityGraphs

## Overview
This repository contains code and data related to classifying (Dis)ordered Structures as Superionic Lithium Conductors.

## Repository Structure

### Notebooks

- **Step_1_Clean_and_Featurize_Labelled_Data.ipynb**:  
  Cleans and processes labeled data, extracting relevant features for further analysis. It ensures that the labeled data is in a suitable format for model training.
  
- **Step_2_Cluster_and_Generate_Train_Val_Test_Splits.ipynb**:  
  Clusters the labeled data to generate train, validation, and test splits, ensuring models generalize well across different material groups.
  
- **Step_3_Generate_Controls.ipynb**:  
  Generates control datasets to validate the robustness of the models by introducing synthetic or alternate datasets for comparison.

- **Step_4_Featurize_Unlabelled_Data.ipynb**:  
  Processes the unlabeled data, extracting the same features as the labeled dataset for later prediction.

- **Step_5_KFold_Validation.ipynb**:  
  Performs K-Fold cross-validation on the training data to evaluate model performance across different data splits, helping prevent overfitting.

- **Step_7_Leave_One_Cluster_Out_Cross_Validation_Analysis.ipynb**:  
  Implements leave-one-cluster-out cross-validation to validate models with material clusters excluded once during testing.

- **Step_8_Test_Validation.ipynb**:  
  Handles the final validation and testing of the trained models on unseen data to estimate true performance.

- **Step_9_Predict_on_Unlabelled_Data.ipynb**:  
  Applies the trained models to predict ionic conductivity of materials in the unlabeled dataset after training and validation.

### Scripts

- **`hpo_classification.py`**:  
  This script performs hyperparameter optimization (HPO) for classification models predicting superionic conductivity in materials. It uses Ray Tune for HPO and supports different input feature types like MEGNet and M3GNet.

- **`hpo_classification_training_top_configurations_repeated_runs.py`**:  
  This script performs repeated runs of training using the top configurations identified from hyperparameter optimization (HPO) for classification of superionic materials. It saves model histories and results for each run.

- **`model_training.py`**:  
  This script handles the training of AtomSets models using K-fold cross-validation. It supports the use of pre-trained models and various input feature types.

- **`data_analysis.py`**:  
  This script analyzes the training results, including extracting the best epochs, calculating averages and standard deviations for K-fold cross-validation, and managing control metrics for model evaluation.

- **`data_featurization.py`**:  
  This script handles data featurization, including loading structures from CIF files, simplifying structures, generating MEGNet-compatible graphs, and calculating structural features for use in machine learning models.

### Figures

- Include any relevant figures or plots generated by the notebooks or scripts in this directory.

### Data

- **Labelled Data**:  
  Preprocessed data containing labeled materials with known ionic conductivity values.

- **Unlabelled Data**:  
  Raw data for materials without labeled ionic conductivity, which is used for predictions.

### MAML (Materials Learning Model)

- **maml/models**:  
  This directory contains the pre-trained models for various machine learning architectures, including `AtomSets` and `MLP`, used throughout the project.
