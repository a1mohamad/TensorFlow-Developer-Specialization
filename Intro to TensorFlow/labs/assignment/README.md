# 📁 README: C1W4_Assignment - Happy or Sad Dataset

This repository contains the solution for **Week 4: Handling Complex Images** assignment from the **TensorFlow Developer Certificate Program (Course 1)**.

The assignment focuses on building a **Convolutional Neural Network (CNN)** for binary classification and implementing a **custom Keras Callback** to manage the training lifecycle.

---

## 🎯 Assignment Objectives

The primary goals of this assignment are:

- **High Accuracy:** Create a CNN model capable of achieving **99.9% training accuracy** on the small dataset.  
- **Early Stopping Callback:** Implement a custom `tf.keras.callbacks.Callback` to automatically halt training immediately upon reaching the 99.9% accuracy target.

---

## 🖼️ Dataset: Happy or Sad

The model is trained on the simple **"Happy or Sad"** image dataset.

| Feature | Details |
|----------|----------|
| **Classes** | 2 (Binary Classification: Happy or Sad) |
| **Total Images** | 80 images (40 happy, 40 sad) |
| **Input Shape** | (150, 150, 3) - 150x150 resolution with 3 RGB color channels |
| **Data Source** | Local file system, organized into `./data/happy/` and `./data/sad/` subdirectories |

---

## 🛠️ Implementation Details

The solution involves three core components: the **Callback**, the **Dataset**, and the **Model Architecture**.

---

### 1. Custom Callback (`EarlyStoppingCallback`)

A custom callback class is defined to monitor the training accuracy and stop the process programmatically.

```python
class EarlyStoppingCallback(tf.keras.callbacks.Callback):
    def on_epoch_end(self, epoch, logs=None):
        if logs['accuracy'] >= 0.999:
            self.model.stop_training = True
            print("\nReached 99.9% accuracy so cancelling training!")
```
## 🧠 2. Data Preparation (`training_dataset`)

Data preparation is a crucial part of this assignment. The dataset is small but still requires proper preprocessing to ensure consistent input to the CNN model.

### 📦 Steps Overview

- **Loader:** Images are loaded from the local directory using `tf.keras.utils.image_dataset_from_directory`, which automatically labels data based on folder names (`happy/` and `sad/`).  
- **Normalization:** Pixel values are rescaled from **[0, 255]** to **[0.0, 1.0]** using a `tf.keras.layers.Rescaling` layer applied via the `.map()` function.  
- **Labeling:** `label_mode='binary'` is specified to handle binary classification.

### 🧩 Example Code

```python
import tensorflow as tf

# Load dataset
train_dataset = tf.keras.utils.image_dataset_from_directory(
    directory='./data/',
    image_size=(150, 150),
    batch_size=8,
    label_mode='binary'
)

# Normalize pixel values
normalization_layer = tf.keras.layers.Rescaling(1./255)
train_dataset = train_dataset.map(lambda x, y: (normalization_layer(x), y))
```

### 3. Model Architecture (`create_and_compile_model`)

The model is a sequential CNN designed to efficiently learn features from the 150×150 color images.

| **Layer Type** | **Configuration** | **Purpose** |
|----------------|------------------|--------------|
| Input | (150, 150, 3) | Defines input shape |
| Conv2D | 16 filters, (3×3) kernel, `'gelu'` activation | Initial feature detection |
| MaxPooling2D | (2×2) pool size | Downsampling |
| Conv2D | 32 filters, (3×3) kernel, `'gelu'` activation | Deeper feature detection |
| MaxPooling2D | (2×2) pool size | Downsampling |
| Conv2D | 64 filters, (3×3) kernel, `'gelu'` activation | Final convolutional stage |
| MaxPooling2D | (2×2) pool size | Final downsampling |
| Flatten | — | Prepares feature maps for the dense layers |
| Dense | 512 units, `'gelu'` activation | Intermediate dense layer |
| Dense | 1 unit, `'sigmoid'` activation | Final output for binary classification |

**Compilation Parameters:**

- **Loss:** `tf.keras.losses.BinaryCrossentropy()` (compatible with 1-unit Sigmoid output)  
- **Optimizer:** `tf.keras.optimizers.RMSprop(learning_rate=1e-3)` (used instead of Adam, as suggested in tips)  
- **Metrics:** `['accuracy']` (required for the callback)
