## Image Data Preprocessing Lab - Horses or Humans 🐴🧍 (Simplified)

This lab details essential **image data preprocessing techniques** for efficiently training a Convolutional Neural Network (CNN) on the **Horses or Humans** dataset.

***

### Key Objectives

1.  **Build a CNN** for **binary classification** (Horse vs. Human).
2.  **Load and Label Images** efficiently using `tf.keras.utils.image_dataset_from_directory`.
3.  **Normalize Pixel Values** (from $\left[0, 255\right]$ to $\left[0, 1\right]$) with the `tf.keras.layers.Rescaling` layer.
4.  **Optimize the Data Pipeline** for faster training using `cache()`, `shuffle()`, and `prefetch()`.

***

### Dataset Access Limitation

The **Horses or Humans** dataset is **not uploaded** here due to size limitations.

You can use the dataset through **TensorFlow Datasets (TFDS)**:

➡️ **`tfds.image_classification.HorsesOrHumans`**

The official TFDS implementation file is located at: [https://github.com/tensorflow/datasets/tree/master/tensorflow_datasets/image_classification/horses_or_humans.py](https://github.com/tensorflow/datasets/tree/master/tensorflow_datasets/image_classification/horses_or_humans.py)

***

### Model and Preprocessing Summary

| Component | Detail |
| :--- | :--- |
| **Model Type** | Sequential CNN for $300\times300$ images. |
| **Final Layer** | Dense(1) with **`sigmoid`** activation. |
| **Compilation** | `loss='binary_crossentropy'`, `optimizer=RMSprop(0.001)`. |
| **Normalization** | Pixels rescaled by **$1/255$** to the $\left[0, 1\right]$ range. |
| **Optimization** | **`cache()`**, **`shuffle()`**, and **`prefetch()`** are used on the `tf.data.Dataset` for faster data loading. |

***

### Outcome

The lab demonstrates how to achieve good **accuracy** through effective data preparation, followed by steps to **test custom images** and **visualize feature maps** learned by the CNN.