# Multi-Task-Attention-Network

This repository contains the implementation of the **Multi-Task Attention Network (MTAN)** for the CityScapes dataset. The MTAN model is designed to perform multi-task learning, specifically for **semantic segmentation** and **depth estimation** tasks simultaneously. The model leverages shared features and task-specific attention mechanisms to improve performance across both tasks.

## Overview

The **Multi-Task Attention Network (MTAN)** is a deep learning model that performs two tasks simultaneously:
1. **Semantic Segmentation**: Classifying each pixel in an image into one of 19 predefined classes (e.g., road, car, pedestrian).
2. **Depth Estimation**: Predicting the depth (distance) of each pixel from the camera.

The model uses a shared encoder-decoder architecture with task-specific attention modules to dynamically allocate resources to each task, improving overall performance.


## Key Features
- **Multi-Task Learning**: Simultaneously performs semantic segmentation and depth estimation.
- **Attention Mechanism**: Task-specific attention modules improve feature sharing and task performance.
- **Dynamic Weight Adjustment**: Uses Dynamic Weight Average (DWA) to balance losses across tasks during training.
- **CityScapes Dataset**: Trained and evaluated on the CityScapes dataset, a benchmark for urban scene understanding.


## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/mtan-cityscapes.git
   cd mtan-cityscapes
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Download the CityScapes dataset and place it in the `data` directory. The dataset should have the following structure:
   ```
   data/
   ├── train/
   │   ├── image/
   │   ├── label/
   │   └── depth/
   └── val/
       ├── image/
       ├── label/
       └── depth/
   ```


## Dataset

The CityScapes dataset is used for training and evaluation. It contains:
- **Images**: High-resolution urban scene images.
- **Semantic Labels**: Pixel-wise annotations for 19 classes.
- **Depth Maps**: Ground truth depth information.

Download the dataset from the [CityScapes website](https://www.cityscapes-dataset.com/).


## Training

To train the MTAN model, run the following command:
```python
python train.py
```

### Training Configuration
- **Batch Size**: 8
- **Epochs**: 100
- **Learning Rate**: 1e-3 (with StepLR scheduler)
- **Loss Balancing**: Dynamic Weight Average (DWA)

### Training Output
The training process logs the following metrics for each epoch:
- **Semantic Segmentation Loss**
- **Mean IoU (Intersection over Union)**
- **Pixel Accuracy**
- **Depth Estimation Loss**
- **Absolute Error**
- **Relative Error**

---

## Testing

To evaluate the trained model on the validation set, run:
```python
python test.py
```

### Testing Output
The testing process generates:
- **Semantic Segmentation Predictions**: Visualized as overlays on the input images.
- **Depth Estimation Predictions**: Visualized as depth maps.

---

## Results

### Semantic Segmentation
- **Mean IoU**: ~75%
- **Pixel Accuracy**: ~95%

### Depth Estimation
- **Absolute Error**: ~0.015
- **Relative Error**: ~25%

### Sample Predictions
- **Semantic Segmentation**:
  ![Segmentation Example](results/segmentation_example.png)
- **Depth Estimation**:
  ![Depth Example](results/depth_example.png)

---

## References
- **MTAN Paper**: [Multi-Task Attention Network](https://arxiv.org/abs/1803.10704)
- **CityScapes Dataset**: [CityScapes Dataset](https://www.cityscapes-dataset.com/)
- **Original GitHub Implementation**: [lorenmt/mtan](https://github.com/lorenmt/mtan)

---
