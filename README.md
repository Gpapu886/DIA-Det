# DIA-Det

This repository contains the model configurations and experimental results associated with the manuscript:

**DIA-Det: A Dynamic Upsampling and iEMA-Enhanced Detector for Fine-Grained Pediatric Dental Caries Detection From Smartphone Images**

## Overview

DIA-Det is a lightweight object detector developed for fine-grained pediatric dental caries detection from smartphone intraoral images.

The model is based on YOLOv8n and introduces:

- **DySample-based dynamic upsampling** for adaptive reconstruction of lesion-related spatial details.
- **iRMB-EMA feature enhancement** for improving feature selection under reflections, shadows, and complex oral backgrounds.

The model retains the original P3, P4, and P5 detection outputs of YOLOv8.

## Dataset

The experiments were conducted on a pediatric smartphone intraoral image dataset containing:

- 6,205 images
- 64,932 annotated instances
- Seven ICDAS-related categories:
  - `no_caries`
  - `caries_1`
  - `caries_2`
  - `caries_3`
  - `caries_4`
  - `caries_5`
  - `caries_6`

The original images are not publicly available because they contain clinical image data from pediatric participants and are subject to institutional privacy restrictions.

## Main Results

| Model | Params (M) | GFLOPs | Precision | Recall | F1-score | mAP@0.5 | mAP@0.5:0.95 |
|---|---:|---:|---:|---:|---:|---:|---:|
| YOLOv8n | 3.007 | 8.1 | 0.867 | 0.805 | 0.835 | 0.891 | 0.652 |
| YOLOv8n + DySample | 3.019 | 8.1 | 0.862 | 0.832 | 0.847 | **0.899** | **0.662** |
| YOLOv8n + iEMA | 3.116 | 8.3 | 0.852 | 0.825 | 0.838 | 0.891 | 0.656 |
| **CariesDIA-YOLO** | **3.096** | **8.2** | 0.862 | **0.836** | **0.849** | 0.898 | 0.660 |

CariesDIA-YOLO achieved the highest recall and F1-score among the evaluated variants while maintaining a lightweight computational profile.

## Experimental Environment

- Python 3.8
- PyTorch 2.1.0
- Ultralytics YOLOv8.2.18
- NVIDIA GeForce RTX 4080 Laptop GPU
- Input size: 640 × 640
- Training epochs: 200

## Repository Contents

This repository provides:

- YOLO model configuration files
- DIA-Det configuration
- Training and evaluation scripts
- Ablation experiment settings
- Summarized experimental results
- Figure and table generation utilities

## Data Availability

The original pediatric oral-image dataset cannot be publicly released because of privacy and institutional restrictions.

De-identified evaluation summaries, model configuration files, and analysis scripts are provided to support reproducibility.

## Citation

The corresponding manuscript is currently under review.

