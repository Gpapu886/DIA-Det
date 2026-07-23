# DIA-Det

This repository accompanies the manuscript:

**DIA-Det: A Dynamic Upsampling and iEMA-Enhanced Detector for Fine-Grained Pediatric Dental Caries Detection From Smartphone Images**

## Overview

DIA-Det is a lightweight YOLOv8n-based detector for fine-grained pediatric dental caries detection from smartphone intraoral images.

The model introduces:

- **DySample** in the two neck upsampling stages for adaptive feature reconstruction.
- **iEMA** before SPPF in the deepest backbone stage.
- **C2f-iEMA** blocks in the P3 and P4 feature-fusion pathways.

The original P3, P4, and P5 detection outputs are retained.

## Dataset

The study used **1,241 original de-identified pediatric intraoral images** obtained from a hospital dataset.

The images were divided before augmentation into:

| Subset | Images |
|---|---:|
| Training | 868 |
| Validation | 186 |
| Test | 187 |

Data augmentation was applied only to the training subset, expanding it to **6,205 training images** with **64,932 annotated instances** across seven ICDAS-related categories:

- `no_caries`
- `caries_1`
- `caries_2`
- `caries_3`
- `caries_4`
- `caries_5`
- `caries_6`

The original clinical images are not publicly released because of institutional privacy restrictions.

## Main Results

| Model | Params (M) | GFLOPs | Precision | Recall | F1-score | mAP@0.5 | mAP@0.5:0.95 |
|---|---:|---:|---:|---:|---:|---:|---:|
| YOLOv8n | 3.007 | 8.1 | **0.867** | 0.805 | 0.835 | 0.891 | 0.652 |
| YOLOv8n + DySample | 3.019 | 8.1 | 0.862 | 0.832 | 0.847 | **0.899** | **0.662** |
| YOLOv8n + iEMA | 3.116 | 8.3 | 0.852 | 0.825 | 0.838 | 0.891 | 0.656 |
| **DIA-Det** | **3.096** | **8.2** | 0.862 | **0.836** | **0.849** | 0.898 | 0.660 |

DIA-Det achieved the highest recall and F1-score among the evaluated variants while maintaining a lightweight computational profile.

## Repository Contents

This repository provides the network configuration files used for:

- YOLOv8n baseline
- YOLOv8n + DySample
- YOLOv8n + iEMA
- DIA-Det

## Environment

- Python 3.8
- PyTorch 2.1.0
- Ultralytics YOLOv8.2.18
- NVIDIA GeForce RTX 4080 Laptop GPU
- Input size: 640 × 640
- Training epochs: 200

## Data Availability

The original hospital image dataset cannot be publicly shared because it contains clinical images from pediatric participants and is subject to institutional privacy restrictions. All images used for computational analysis were de-identified.

## Contact
Email: houchao@sspu.edu.cn
