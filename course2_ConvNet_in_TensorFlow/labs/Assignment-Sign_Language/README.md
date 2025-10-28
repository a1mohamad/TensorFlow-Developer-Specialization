# Multi-class Sign Language Classifier

---

## 🚀 Project Overview: Model Development & Workflow

This document provides a technical breakdown of the multi-class image classification assignment notebook (`C2W4_Assignment.ipynb`). The project goal is to build a high-performance **Convolutional Neural Network (CNN)** to classify 24 distinct hand signs from the Sign Language MNIST dataset.

The solution is divided into three critical, sequential processes: **Data Ingestion, Model Architecture, and Training Configuration.**

---

## 1. 🖼️ Data Ingestion and Preprocessing

The primary challenge is preparing the images from the file system for consumption by the TensorFlow model.

### **Data Access & Limitations:**

* **Dataset:** Modified Sign Language MNIST (24 classes: A-Y, excluding J, Z).
* **File Format:** 28x28 grayscale images pre-sorted into class directories.
* **LIMITATION:** The dataset files are **NOT** included in this repository.

### **Ingestion Process:**

The data is loaded and structured using the **`tf.data.Dataset`** API:

1.  **Directory Reading:** The notebook uses `tf.keras.utils.image_dataset_from_directory` to read image files directly from the local `./data/train/` and `./data/validation/` folders.
2.  **Image Scaling:** All image pixel values (0-255) are **rescaled** to floating-point numbers between 0 and 1, a standard practice for neural networks.
3.  **Data Augmentation:** A **Data Augmentation** pipeline is applied to the training set to artificially increase dataset size and improve model robustness against minor variations. Common augmentations used here include:
    * Randomly flipping images horizontally.
    * Randomly rotating, zooming, or shifting images.

---

## 2. 🧠 Model Architecture (CNN Design)

The assignment requires defining a robust sequential CNN model to extract features from the 28x28 input images.

### **Input Layer:**

* **Shape:** `(28, 28, 1)` (Height, Width, Color Channel (grayscale)).

### **Feature Extraction (Convolutional Blocks):**

* The model typically uses a sequence of blocks, each containing:
    1.  **`Conv2D`:** Convolutional layers with filters (e.g., 32, 64) and an activation function like **`ReLU`**.
    2.  **`MaxPooling2D`:** Downsampling the feature map to reduce dimensionality and computational load.
* **Regularization:** **`Dropout`** layers are strategically placed after pooling to randomly deactivate neurons, preventing the model from becoming overly dependent on specific features.

### **Classification Head:**

1.  **`Flatten`:** The final 2D feature map is converted into a 1D vector.
2.  **`Dense`:** One or more fully connected layers process the flattened features.
3.  **Output Layer:**
    * **Neurons:** **24** (one for each class).
    * **Activation:** **`softmax`** (converts raw scores into a probability distribution where the sum of all 24 probabilities equals 1).

---

## 3. 📉 Training Configuration

The model is compiled with the correct loss function and metrics required for a multi-class task with integer labels.

* **Loss Function:** **`sparse_categorical_crossentropy`**
    * *Why?* This is the mathematically correct loss function when the true labels are provided as **integers** (0, 1, 2, ..., 23) rather than one-hot encoded vectors.
* **Optimizer:** An efficient gradient-based optimizer (e.g., **Adam**) is used to minimize the loss function.
* **Metrics:** **`accuracy`** is tracked on both the training and validation sets to monitor model performance and detect overfitting.

---