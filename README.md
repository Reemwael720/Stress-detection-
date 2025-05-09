# Stress-detection

# ECG Stress Classification using LSTM and CNN

This project is designed to classify ECG signals into two categories: **Stress** and **Non-Stress**. The classification is based on the **WESAD** dataset, which includes physiological signals from individuals in different emotional states. The classification is carried out using a combination of **Convolutional Neural Networks (CNN)** and **Long Short-Term Memory (LSTM)** networks to take advantage of both feature extraction (via CNN) and sequence learning (via LSTM).

## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Installation](#installation)
- [Data Preprocessing](#data-preprocessing)
- [Model Architecture](#model-architecture)
- [Training and Evaluation](#training-and-evaluation)
- [Results](#results)


## Overview

This project explores the use of deep learning techniques to classify ECG signals collected from participants experiencing different emotional states. The WESAD dataset includes continuous ECG recordings from subjects undergoing stress, amusement, meditation, and other conditions. By preprocessing the data and applying a CNN + LSTM-based model, we can classify these signals into stress (1) or non-stress (0) categories.

Key components of the project:
- **Data cleaning and preprocessing**.
- **Balancing the dataset** using undersampling and SMOTE to handle class imbalance.
- **Model building** using CNN for feature extraction and LSTM for sequence prediction.
- **Evaluation** using accuracy, confusion matrix, and classification reports.


### Dataset 
The dataset consists of `.pkl` files for each participant, where each file contains physiological signals, including ECG. The signals are organized into a dictionary with keys like `signal` (for the actual signals) and `label` (for the emotional state labels). 

The labels are:
- **0**: Not defined
- **1**: Baseline
- **2**: Stress
- **3**: Amusement
- **4**: Meditation
- **5-7**: Additional states

## Project Workflow
1. **Data Loading**
   - Load `.pkl` files and extract ECG signal from S2 $ S17.
   - ![Distribution]https://github.com/user-attachments/assets/79bc7a16-28b2-43e3-8a90-fc8fd73aaed7)

2. **Preprocessing**
   - Removal of zero-value artifacts.
   - Label filtering and binary mapping:
     - `2` → Stress → `1`
     - Others (`1`, `3`, `4`) → Non-stress → `0`
