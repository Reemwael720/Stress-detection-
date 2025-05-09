# Stress-detection

# ECG Stress Classification using LSTM and CNN

This project is designed to classify ECG signals into two categories: **Stress** and **Non-Stress**. The classification is based on the **WESAD** dataset, which includes physiological signals from individuals in different emotional states. The classification is carried out using a combination of **Convolutional Neural Networks (CNN)** and **Long Short-Term Memory (LSTM)** networks to take advantage of both feature extraction (via CNN) and sequence learning (via LSTM).

## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Data Loading](#data-loading)
- [Data Preprocessing](#data-preprocessing)
- [Model Architecture](#model-architecture)
- [Training](#training)
- [Evaluation](#Evaluation)
- [Results](#results)


## Overview

This project explores the use of deep learning techniques to classify ECG signals collected from participants experiencing different emotional states. The WESAD dataset includes continuous ECG recordings from subjects undergoing stress, amusement, meditation, and other conditions. By preprocessing the data and applying a CNN + LSTM-based model, we can classify these signals into stress (1) or non-stress (0) categories.

Key components of the project:
- **Data cleaning and preprocessing**.
- **Balancing the dataset** using undersampling and SMOTE to handle class imbalance.
- **Model building** using CNN for feature extraction and LSTM for sequence prediction.
- **Evaluation** using accuracy, confusion matrix, and classification reports.


## Dataset 
The dataset consists of `.pkl` files for each participant, where each file contains physiological signals, including ECG. The signals are organized into a dictionary with keys like `signal` (for the actual signals) and `label` (for the emotional state labels). 

The labels are:
- **0**: Not defined
- **1**: Baseline
- **2**: Stress
- **3**: Amusement
- **4**: Meditation
- **5-7**: Additional states

## Data Loading
   - Load `.pkl` files and extract ECG signal from S2 & S17.
   -  Label filtering and binary mapping:
       - `2` → Stress → `1`
       - Others (`1`, `3`, `4`) → Non-stress → `0`
      
 <p align="center">
   <img src= "https://github.com/user-attachments/assets/a94d62e6-31db-4002-b456-51f76afd00de" alt="Destribution">
 </p>
 
## Data Preprocessing
   - Removal of zero-value artifacts.
   - Sliding window approach (5-second windows: 3500 samples)
   - 50% overlap with majority label voting
   - Used `neurokit2.ecg_clean()` for noise filtering
   - Under-sampling + SMOTE to address class imbalance
     
   -  ![preprocessing](https://github.com/user-attachments/assets/0449d3d2-6be6-4df9-9cb1-e938f1fff1b0)

## Model Architecture
   - Deep **1D CNN** model with:
     - 5 convolutional layers
     - BatchNormalization & Dropout for regularization
     - Fully connected dense layers
   - Final layer: Sigmoid activation for binary classification

## Training
   - Loss: Binary Crossentropy
   - Optimizer: Adam
   - Epochs: 30
   - Batch Size: 16

## Evaluation
   - Accuracy, Confusion Matrix, Classification Report
   - Training vs. Validation curves

 <p align="center">
   <img src= "https://github.com/user-attachments/assets/1d78bd1b-55b8-438c-85bd-25defe19fbc7" alt="loss & accuracy">
 </p>


<!-- Contributors -->
## <img  align= center width=50px height=50px src="https://media1.giphy.com/media/WFZvB7VIXBgiz3oDXE/giphy.gif?cid=6c09b952tmewuarqtlyfot8t8i0kh6ov6vrypnwdrihlsshb&rid=giphy.gif&ct=s"> Contributors <a id = "contributors"></a>

<!-- Contributors list -->
<table align="center" >
  <tr>
        <td align="center"><a href="https://github.com/Reem463"><img src="https://avatars.githubusercontent.com/u/181993417?v=4" width="150px;" alt=""/><br /><sub><b>Reem Al Ghazali </b></sub></a><br /></td>
       
  </tr>
</table>
