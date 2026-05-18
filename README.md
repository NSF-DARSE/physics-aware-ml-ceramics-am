## [![License: BSD-3-Clause](https://img.shields.io/badge/License-BSD--3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)
# Case Study: Physics-Aware Microstructure Learning with Pretrained Models

## Overview

This project explores **segmentation of microstructure images** using a combination of:

- classical image processing (for pseudo-label generation)
- deep learning (for learned segmentation)

Since annotated ground truth masks are unavailable, we adopt a **pseudo-labeling approach**, where thresholding methods generate approximate labels, which are then used to train a segmentation model.

## Objectives

The current stage of the project focuses on:

1. Building a **baseline pseudo-labeling pipeline**
2. Training segmentation models, including **pretrained-model-based approaches**
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
├── codes/                  # Experimental or previous versions
├── construction_codes/     # preliminary construction attempts
├── segmentation/           # Main segmentation pipeline
│   ├── 1200/               # Experiments for 1200°C dataset
│   │   ├── segmentation_1200_otsu.ipynb
│   │   └── segmentation_1200_sauvola.ipynb  #segmentation with two different thresholding
│   ├── 1400/               # Experiments for 1400°C dataset
│   │   ├── segmentation_1400_otsu.ipynb
│   │   └── segmentation_1400_sauvola.ipynb
│
├── requirements.txt        # Python dependencies
└── README.md
```

## Getting Started
## Install all the dependencies

`pip install -r requirements.txt`

## Testing Strategy

- Tested multiple segmentation models:
  - Baseline CNN
  - U-Net
  - DINOv2 + Decoder

- Evaluated different training settings:
  - 20, 40, and 100 epochs
  - Different train-test splits

- Compared pseudo-label generation methods:
  - Otsu Thresholding
  - Sauvola Thresholding

- Verified preprocessing pipeline:
  - Image cropping
  - Resizing to 224×224
  - Binary mask generation

- Evaluated segmentation performance using:
  - Training loss
  - Dice score
  - IoU score
  - Pixel accuracy

- Performed qualitative validation through visual comparison of:
  - Original images
  - Generated masks
  - Predicted segmentation outputs

- Resource profiling performed on DARWIN HPC GPU environment.

## Documentation
This repository includes an optional Sphinx documentation scaffold.

## Contributing
All changes must go through pull requests.
