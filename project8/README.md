# Traffic Sign Recognition System

## Overview
A deep learning project that classifies traffic signs from images into 43 categories using Convolutional Neural Networks (CNN). The project compares a Dense neural network baseline against a CNN architecture, demonstrating why spatial feature extraction is critical for image classification tasks.

## Dataset
- **Source:** Kaggle (German Traffic Sign Recognition Benchmark — GTSRB)
- **Training images:** 39,209
- **Test images:** 12,630
- **Classes:** 43 traffic sign types (speed limits, stop, yield, pedestrian crossings, etc.)
- **Image size:** Resized to 30×30 pixels (RGB)

## Approach

### 1. Data Preprocessing
- Loaded all training and test images using PIL
- Resized all images to a uniform 30×30×3 (RGB) shape
- Normalised pixel values to [0, 1] by dividing by 255
- Shuffled data and split into training (90%) and validation (10%) sets using stratified splitting to preserve class distribution

### 2. Exploratory Data Analysis
- Visualised class distribution across all 43 categories to check for imbalance
- Displayed random sample images from the training and test sets
- Plotted sample predictions alongside actual labels to verify model output

### 3. Model 1 — Dense Neural Network (Baseline)
**Architecture:**
- Flatten → Dense (300, ReLU) → BatchNorm → Dropout (0.5)
- Dense (300, ReLU) → BatchNorm → Dropout (0.5)
- Dense (43, Softmax)

**Results:**
- Training accuracy: ~96%
- Validation accuracy: ~95%
- **Test accuracy: 83%**

The large gap between validation and test performance indicated the model was not generalising — flattening the image before processing destroyed spatial relationships between pixels, making it unable to handle the variation in the unseen test set.

### 4. Model 2 — CNN (Final Model)
**Architecture:**
- Conv2D (16 filters, 3×3) → Conv2D (32 filters, 3×3) → MaxPool (2×2) → BatchNorm
- Conv2D (64 filters, 3×3) → Conv2D (128 filters, 3×3) → MaxPool (2×2) → BatchNorm
- Flatten → Dense (512, ReLU) → BatchNorm → Dropout (0.5)
- Dense (43, Softmax)

**Results:**
- Training accuracy: ~99.7%
- Validation accuracy: ~99.6%
- **Test accuracy: 96.4%**

The CNN preserved spatial structure through convolutional filters and pooling layers, enabling it to learn local patterns (edges, shapes) that generalise far better to unseen data.

### 5. Evaluation
- Compared training and validation loss/accuracy curves for both models
- Generated a 43×43 confusion matrix heatmap to visualise per-class performance
- Visualised individual test predictions alongside ground truth labels

## Key Findings
- The Dense network failed to generalise (83% test accuracy) because flattening destroys spatial pixel relationships critical for image recognition
- Switching to a CNN architecture improved test accuracy by over 13 percentage points (83% → 96.4%)
- The CNN's convolutional layers successfully learned hierarchical spatial features — edges in early layers, complex sign shapes in deeper layers
- BatchNormalization and Dropout were effective at stabilising training and preventing overfitting across both architectures

## Tech Stack
- **Python** — NumPy, Pandas
- **TensorFlow / Keras** — Model building and training
- **Scikit-learn** — Train/test splitting, confusion matrix
- **Visualisation** — Matplotlib, Seaborn
- **PIL (Pillow)** — Image loading and resizing

## How to Run
1. Clone the repository
2. Install dependencies: `pip install numpy pandas tensorflow scikit-learn matplotlib seaborn Pillow`
3. Ensure the `Train/` and `Test/` image directories are in the working directory
4. Open `Traffic_sign_recognition.ipynb` in Jupyter Notebook
5. Run all cells top to bottom
