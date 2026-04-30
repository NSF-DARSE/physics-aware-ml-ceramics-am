# Microstructure Segmentation

## Overview

This section implements a **baseline segmentation pipeline** for microstructure images using **pseudo-labeling** and a simple convolutional neural network (CNN).

Since ground truth segmentation masks are not available, we generate **pseudo-labels** using classical image processing techniques and use them to train a segmentation model.
