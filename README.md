# Multi-Stream CNN and Knowledge Distillation for Behavioral Ransomware Detection

We propose a multi-stream convolutional neural network (CNN) architecture where each input stream corresponds to one of 8 disk I/O features. A high-capacity teacher model is trained first, and then a lightweight student model is distilled from it using both logit-level and feature-level supervision.

## Overview

We present a multi-stream CNN framework where each stream independently processes one of 8 temporal disk I/O features. A high-capacity teacher model is first trained, and a lightweight student model is then learned using knowledge distillation, combining both logit-level and feature-level supervision.

## Features

- **Dataset**: RanSAP (disk I/O logs from ransomware and benign apps) (Link https://github.com/manabu-hirano/RanSAP)
- **Input Format**: Time-series samples of shape `(T, 8)`
- **Models**:
  - **Teacher**: 8-stream CNN with residual blocks
  - **Student**: Lightweight CNN with distillation
- **Loss Function**: CE + KL Divergence + MSE


## Setup

Install dependencies:

```bash
pip install -r requirements.txt
```
## Feature Extraction

feature_extraction.ipynb performs calculating the 8 features, along with per-class normalization and split the dataset into train/test/validation. The user can define the detection time and window size as neccesary.
list of features:
- Read Throughput
- Write Throughput
- Read Variance-like Logical Block Address
- Write Variance-like Logical Block Address
- Average Entropy
- Entropy variance
- Read Spatial Locality Ratio
- Write Spatial Locality Ratio
## Model training

The main contribution for this research is multi-stream CNN that each stream take 1D input as a teacher model, follow throug knowledge distillation into lightweight student model suitable for constrained-environment. For ablation study, we also perform using 5 original features dereived from the RanSAP's author. In addition, we also conduct experiment by performing cross-architecture on the teacher model; consist of transformer, AutoEncode, DNN, and MLP-mixer. The pre-trained model is also given.
