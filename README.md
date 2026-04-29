# Case Study: Physics-Aware Microstructure Learning with Pretrained Models

## Overview

This project explores **segmentation of microstructure images** using a combination of:

- classical image processing (for pseudo-label generation)
- deep learning (for learned segmentation)

Since annotated ground truth masks are unavailable, we adopt a **pseudo-labeling approach**, where thresholding methods generate approximate labels, which are then used to train a segmentation model.

## Objectives

The current stage of the project focuses on:

1. Building a **baseline pseudo-labeling pipeline**
2. Training a **pre-trained segmentation models**
3. Evaluating models behavior against noisy labels
4. Designing a **modular and reproducible pipeline**

## Pipeline Summary

```text
Raw TIFF Images
    ↓
Preprocessing (crop, resize)
    ↓
Pseudo Mask Generation (Otsu vs. Sauvola)
    ↓
Segmentation Models (Simple CNN, U-Net, DINOv2)
    ↓
Predicted Masks
```

## Repository Structure
```
├── papers/                 # Related research papers
├── old_codes/              # Experimental or previous versions
├── segmentation/           # Main segmentation pipeline
│   ├── 1200/               # Experiments for 1200°C dataset
│   │   ├── segmentation_1200.ipynb
│   │   └── segmentation_1200_sau.ipynb  #segmentation with two different thresholding
│   ├── 1400/               # Experiments for 1400°C dataset
│   │   ├── segmentation_1400.ipynb
│   │   └── segmentation_1400_sau.ipynb
│
├── requirements.txt        # Python dependencies
└── README.md
```

## Getting Started
## Install all the dependencies

`pip install -r requirements.txt`

## Documentation
This repository includes an optional Sphinx documentation scaffold.

## Contributing
All changes must go through pull requests.
