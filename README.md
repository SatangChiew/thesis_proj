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
