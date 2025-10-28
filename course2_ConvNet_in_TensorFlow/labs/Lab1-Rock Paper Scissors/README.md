# Multi-class Image Classifier README

---

## 🚀 Project Overview

This Notebook contains an ungraded Jupyter Notebook (`C2_W4_Lab_1_multi_class_classifier.ipynb`) that demonstrates how to implement a **Convolutional Neural Network (CNN)** for **multi-class image classification**.

The primary focus of this lab is to highlight the **key changes** required to adapt a standard binary classifier to a model capable of distinguishing between **three or more distinct classes**.

### Key Learning Points:

* **Model Architecture:** Adjusting the final output layer for multiple classes.
* **Training Parameters:** Selecting the appropriate loss function and metrics for multi-class tasks.
* **Data Preparation:** Using the `tf.data.Dataset` API to load and preprocess a multi-class dataset.

---

## 🛠 Required Libraries

This project is built using the **TensorFlow** framework. As requested, **no dependency files** (`requirements.txt`, etc.) are included. You will need a Python environment with the following main libraries installed:

* **`tensorflow`**
* **`tensorflow-datasets`**
* **`numpy`**
* **`matplotlib`**
* **`ipywidgets`**

---

## 📚 Dataset Access

The classifier is trained on the **Rock-Paper-Scissors** dataset.

**⚠️ IMPORTANT LIMITATION:**

The image dataset is **not** uploaded to this repository due to file size and storage limitations.

You can easily access and load the dataset directly within the notebook using **TensorFlow Datasets (TFDS)**. Use the following builder to fetch the data:

`tfds.datasets.rock_paper_scissors.Builder`

---

## ⚙️ Multi-Class Concepts

To successfully transition from a binary to a multi-class classifier, the notebook implements two crucial changes:

1.  **Output Layer Activation:** The final layer uses a **`softmax`** activation function (instead of `sigmoid`) to output a probability distribution across all possible classes.
2.  **Loss Function:** The model is compiled with **`sparse_categorical_crossentropy`** (instead of `binary_crossentropy`), which is used when your labels are integers (0, 1, 2, etc.).

---is compiled with \*\*`sparse\_categorical\_crossentropy`\*\* (instead of `binary\_crossentropy`), which is used when your labels are integers (0, 1, 2, etc.).



---

