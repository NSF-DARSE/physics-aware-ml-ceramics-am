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


## Quickstart

1. Clone the repository

```bash
git clone https://github.com/NSF-DARSE/physics-aware-ml-ceramics-am.git
cd physics-aware-ml-ceramics-am
```
2. Install all the dependencies

`pip install -r requirements.txt`

3. Run segmentation experiments from the notebooks inside:
 `segmentation_files/`
 
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

## Resource Profiling

- Experiments were executed on the DARWIN HPC environment using GPU resources.

- Resource usage was monitored during training using terminal-based profiling tools such as:
  - `nvidia-smi`
  - `watch -n 1 nvidia-smi`

- Profiling included:
  - GPU utilization
  - GPU memory usage
  - Training runtime
  - Epoch-level performance tracking

- Resource profiling was compared across:
  - Baseline CNN
  - U-Net
  - DINOv2 + Decoder

- Models were evaluated with different epoch settings (20, 40, and 100 epochs) to analyze computational cost and training stability.

- Input images were resized to 224×224 for consistent GPU processing and model comparison.

## Documentation
This repository includes an optional Sphinx documentation scaffold.

## Contributing
All changes must go through pull requests.
