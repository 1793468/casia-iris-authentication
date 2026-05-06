why reame ,requorements empty in repo # CASIA-Iris-Thousand: Biometric Authentication via ArcFace

This repository contains a deep learning pipeline for an iris recognition system using the **CASIA-Iris-Thousand** dataset. The model leverages a **ResNet-18** backbone combined with **ArcFace (Additive Angular Margin Loss)** to map iris images into a highly discriminative 256-dimensional embedding space.

In this space, images of the *same* iris are tightly clustered, while images of *different* irises are pushed far apart, enabling highly accurate biometric verification and identification.

## Key Features
*   **Metric Learning:** Uses ArcFace (`s=64.0`, `m=0.35`) to optimize the decision boundary for open-set biometric authentication.
*   **Strict Subject-Level Splitting:** Prevents *identity leakage* by ensuring subjects in the validation and test sets are completely unseen during training (80/10/10 split).
*   **Real-World Evaluation Protocol:** Implements a Gallery/Probe evaluation methodology to simulate real-world enrollment and identification.
*   **Robust Augmentation:** Utilizes Albumentations for GPU-friendly image augmentations (GaussNoise, ShiftScaleRotate, CoarseDropout) to handle camera illumination variations and sensor noise.

## Results

The model achieves exceptional performance on a completely held-out test set of 200 unseen subjects:

*   **Top-1 Identification Accuracy:** 98.90%
*   **Verification EER (Equal Error Rate):** 0.65%
*   **Optimal EER Threshold:** 0.3892

*(Note: Add the generated `score_diagnostics.png`, `cmc_curve.png`, and `tsne_clusters.png` to an `iris_results` folder in your repo and link them here to visualize the score distributions and embedding clusters).*

## Dataset

The **CASIA-Iris-Thousand** dataset contains 20,000 near-infrared grayscale iris images from 1,000 subjects. 

**Note:** Due to size and licensing, the dataset is not included in this repository. 
1. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/sondosaabed/casia-iris-thousand/data).
2. Place the extracted `CASIA-Iris-Thousand` folder into the `data/` directory.

## Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/1793468/casia-iris-authentication.git
   cd casia-iris-authenticationtorch