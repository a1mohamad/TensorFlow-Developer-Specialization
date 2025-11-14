# Sarcasm Detection using a 1D Convolutional Layer

## Overview

This notebook contains an Ungraded Lab exercise focused on building a deep learning model for sarcasm detection. The model utilizes a 1D Convolutional Layer (`Conv1D`) for sequence processing, following similar steps to previous labs but with a different core architecture.

## Dataset

* **Source:** The model uses a JSON dataset (`sarcasm.json`).
* **Data Fields:** The dataset contains headlines and a corresponding label (`is_sarcastic`).
* **Split:** The dataset is split into training and test sets.
    * Training Size: 20000 examples
    * Test Size: The remainder of the dataset is used for testing.

## Model Architecture

The deep learning model is a `tf.keras.Sequential` model.

### Key Layers

1.  **Embedding Layer**: Maps integer-encoded vocabulary to dense vectors.
    * Input Dimension (`VOCAB_SIZE`): 10000
    * Output Dimension (`EMBEDDING_DIM`): 16
2.  **Conv1D Layer**: The primary feature extractor for the sequence data.
    * Filters (`FILTERS`): 256
    * Kernel Size (`KERNEL_SIZE`): 6
    * Activation: `relu`
3.  **GlobalMaxPooling1D Layer**: Reduces the dimensionality of the feature maps by taking the maximum value across all time steps.
4.  **Dense Layer**: A intermediate fully-connected layer.
    * Units (`DENSE_DIM`): 6
    * Activation: `relu`
5.  **Output Dense Layer**: The classification layer.
    * Units: 1
    * Activation: `sigmoid` for binary classification

### Training Parameters

* **Loss Function:** `binary_crossentropy`
* **Optimizer:** `adam`
* **Metrics:** `accuracy`
* **Epochs:** 10

## Requirements

The project uses the following Python libraries:

* `json`
* `matplotlib.pyplot` (aliased as `plt`)
* `tensorflow` (aliased as `tf`)

## Results

After 10 epochs of training:

* **Training Accuracy:** The training accuracy quickly reached a very high level (e.g., `0.9998` at Epoch 10), indicating the model learned the training data effectively.
* **Validation Accuracy:** The validation accuracy stabilized, achieving a maximum of approximately `0.8520` in the first epoch and ending around `0.8357`. The gap between training and validation accuracy/loss suggests the model experiences some overfitting.