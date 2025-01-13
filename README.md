# Biomedical Segmentation with U-Net

This project focuses on implementing a U-Net architecture for the segmentation of white blood cells in microscopy images. The aim is to achieve precise pixel-level predictions, making it a valuable tool for biomedical applications.

## Table of Contents
1. [Overview](#overview)
2. [Dataset](#dataset)
3. [Model Architecture](#model-architecture)
4. [Implementation Details](#implementation-details)
5. [Results and Performance](#results-and-performance)
6. [Findings and Insights](#findings-and-insights)

## 1. Overview
### Objective
The goal of this project is to segment individual white blood cells from microscopy images, enabling downstream analysis like counting, classification, and morphological studies.

### Key Highlights
- Achieved a **mean Average Precision (mAP)** of **95.7%**.
- Focused on preprocessing, data augmentation, and hyperparameter tuning to enhance model performance.
- Leveraged U-Net’s encoder-decoder structure for precise segmentation.

## 2. Dataset
### Source
The project used the **Blood Cell Segmentation Dataset**, which includes labeled microscopy images with pixel-wise annotations of cells.

### Statistics
- **Number of Images**: 12,000
- **Image Dimensions**: 256x256 (resized from originals for training efficiency)
- **Classes**: Background, white blood cell

### Preprocessing
- Resized images to a uniform size of 256x256.
- Normalized pixel values to the range [0, 1].
- Applied data augmentation (random flips, rotations, and zooms).

## 3. Model Architecture
The U-Net architecture was chosen for its ability to handle biomedical segmentation tasks effectively.  

### Key Components
1. **Encoder**:
   - Series of convolutional and max-pooling layers to capture features at multiple scales.
2. **Decoder**:
   - Up-convolutional layers to reconstruct the spatial resolution.
3. **Skip Connections**:
   - Combine encoder and decoder features to retain spatial details.

### Customizations
- Added **batch normalization** for better convergence.
- Incorporated **dropout layers** to prevent overfitting.
- Used a **binary cross-entropy with dice loss** for optimization.

## 4. Implementation Details
### Environment
- Framework: PyTorch
- Python: 3.8+
- GPU: NVIDIA Tesla T4 (optional for training)

### Training Parameters
| Parameter         | Value         |
|-------------------|---------------|
| Epochs            | 50            |
| Batch Size        | 16            |
| Learning Rate     | 0.001 (Adam)  |
| Loss Function     | Binary Cross-Entropy + Dice Loss |

## 5. Results and Performance
### Evaluation Metrics
- **Mean Average Precision (mAP)**: 95.7%
- **IoU (Intersection over Union)**: 93.4%
- **Dice Coefficient**: 94.1%

### Qualitative Results
The model successfully segmented cells, with clear boundaries even in images with overlapping or clustered cells.

## 6. Findings and Insights
### Key Learnings
1. **Impact of Data Augmentation**:
   - Improved generalization and robustness to variations in cell shapes and positions.
2. **Loss Function**:
   - Combining Dice Loss with Binary Cross-Entropy yielded better results by balancing precision and recall.
3. **Skip Connections**:
   - Crucial for preserving spatial details, especially for small objects.

### Challenges
- Segmenting overlapping cells required additional post-processing steps, such as connected component analysis.
