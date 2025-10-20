# 📓 ConvNet on Filtered Cat vs. Dog Dataset

This notebook, originally titled `C2\_W1\_Lab\_1\_cats\_vs\_dogs.ipynb`, is a practical exercise from **Course 2: Convolutional Neural Networks in TensorFlow** of the DeepLearning.AI TensorFlow Developer Specialization. It focuses on building a baseline CNN for a real-world image classification task.

## 🎯 Objective

The main objective is to implement and train a **Convolutional Neural Network (CNN)** using the Keras Sequential API to perform **binary classification** (Cat vs. Dog) on a challenging, pre-filtered dataset.

## 💾 Dataset Access

Due to the size constraints, the complete Cat vs. Dog dataset cannot be included directly in the notebook environment. Instead, this lab utilizes a smaller, **filtered subset** of 2,000 images, which can be accessed and downloaded programmatically within the notebook using the following TensorFlow utility:

```python
_URL = '[https://storage.googleapis.com/mledu-datasets/cats_and_dogs_filtered.zip](https://storage.googleapis.com/mledu-datasets/cats_and_dogs_filtered.zip)'
path_to_zip = tf.keras.utils.get_file('cats_and_dogs.zip', origin=_URL, extract=True)
PATH = os.path.join(os.path.dirname(path_to_zip), 'cats_and_dogs_filtered')
```

## 💾 Dataset and Key Implementation Details

## Dataset Overview

The lab utilizes a small, pre-filtered subset of the original **Dogs vs. Cats** dataset. This dataset is structured for binary image classification:

| Data Split | Cat Images | Dog Images | Total Images |
| :--- | :--- | :--- | :--- |
| **Training Data** | 1,000 | 1,000 | **2,000** |
| **Validation Data** | 500 | 500 | **1,000** |

## 🛠 Key Implementation Steps

This notebook covers the fundamental workflow for building a baseline **CNN-based image classifier**:

### Data Ingestion & Preprocessing
* **Data Generator:** Use the **Keras `utils`** with the **`image_dataset_from_directory`** method. This efficiently streams image files from the disk and prepares them for the model.
* **Normalization:** Rescale pixel values (from `0-255` to `0-1`) as a form of **normalization**.
* **Input Configuration:** Configure the image dimensions (size and aspect ratio) to a fixed shape expected by the model.

### Model Architecture
* **CNN Layers:** Define a **Sequential CNN model** incorporating fundamental layers:
    * **Convolutional layers (`Conv2D`):** Learn feature hierarchies from the images.
    * **Max Pooling layers (`MaxPooling2D`):** Downsample the feature maps, reducing dimensionality and making the model more robust to variations.
* **Output Layer:** Flatten the final feature maps and feed them into a standard **Dense** layer with a single output and **`sigmoid`** activation for **binary classification**.

### Training & Evaluation
* **Compilation:** Compile the model using the **RMSprop optimizer** and **`binary_crossentropy`** as the loss function.
* **Training:** Train the model using the `fit` or `fit\_generator` methods.
* **Monitoring:** Observe and plot the training and validation accuracy and loss over epochs.

## ⚠️ The Overfitting Challenge

A critical lesson from this lab is observing the natural tendency of a deep model to **overfit** to limited data. The baseline CNN model will likely exhibit:

* **High Training Accuracy** (model performs well on the data it has seen).
* **Stagnant or Decreasing Validation Accuracy** (model performs poorly on new, unseen data).
* A widening gap between **Training Loss** and **Validation Loss**.

The subsequent labs in the course will focus on introducing advanced techniques like **Data Augmentation**, **Dropout**, and **Transfer Learning** to specifically address and mitigate this overfitting problem.