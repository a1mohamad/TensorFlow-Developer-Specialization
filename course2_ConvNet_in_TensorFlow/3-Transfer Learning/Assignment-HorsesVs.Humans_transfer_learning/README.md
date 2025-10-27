# Week 3: Transfer Learning Assignment - Horse or Human Classifier

This document details the objectives and methodology for the Week 3 assignment, which requires solving an image classification task using the powerful technique of **Transfer Learning**. The goal is to classify images as either a **Horse** or a **Human**.

---

## 🎯 Assignment Objectives

The primary goal is to successfully implement the **Feature Extraction** transfer learning strategy to achieve high accuracy on the target dataset with minimal training time. This involves several critical steps:

1.  **Base Model Configuration**: Utilize a pre-trained Convolutional Neural Network (CNN), such as **InceptionV3**, and load its weights (typically pre-trained on ImageNet).
2.  **Layer Freezing**: Set the convolutional layers of the base model to be **non-trainable** (frozen) to preserve the robust, general features they have already learned.
3.  **Model Customization**: Add a new, small **dense classification head** on top of the frozen base model's output.
4.  **Training**: Train **only** the newly added top layers to adapt the extracted features to the specific binary classification task.

---

## 📊 Dataset: Horse or Human

The assignment uses the **Horse or Human dataset** for training and validation.

### Data Access via TensorFlow Datasets (TFDS)

While the assignment structure might provide data via local files, the dataset is also officially available through the **TensorFlow Datasets (TFDS) catalog**. Using TFDS offers a streamlined, reproducible method for accessing the data directly, simplifying the process of loading, splitting, and preparing the images for the TensorFlow pipeline.

### Data Augmentation

To enhance model generalization and prevent overfitting, especially with a smaller dataset, robust **Data Augmentation** techniques are applied to the training set. These typically include:

* **Rescaling**: Normalizing pixel values to a standard range (e.g., \[0, 1]).
* **Geometric Transformations**: Randomly applying rotations, zooms, and horizontal flips.

---

## 📝 Grading and Submission Notes

Adherence to the submission guidelines is essential for successful grading:

* **Code Submission**: Solution code must be placed exclusively in the **designated cells** within the Jupyter Notebook.
* **Variable Scope**: **Avoid using global variables** unless they are explicitly provided in **UPPERCASE** in the notebook. The grader executes code in an isolated environment where global variables may be unavailable. provided in \*\*UPPERCASE\*\* in the notebook. The grader executes code in an isolated environment where global variables may be unavailable.

