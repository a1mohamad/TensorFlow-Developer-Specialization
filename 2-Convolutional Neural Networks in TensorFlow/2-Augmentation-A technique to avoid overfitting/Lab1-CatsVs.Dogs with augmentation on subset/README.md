# Data Augmentation (Cats vs Dogs)

---

## Project Description

This notebook (`C2_W2_Lab_1_cats_v_dogs_augmentation.ipynb`) is an **ungraded lab** that demonstrates how to implement and use **data augmentation** to combat **overfitting** and improve a deep learning model's performance on unseen data.

Data augmentation artificially increases the variety of the training data through modifications, ensuring the model sees more diverse images during training, which leads to better generalization on new, previously unseen data.

---

## Key Concepts and Tasks

1.  **Baseline Performance:** An initial model with **four convolutional layers** (32, 64, 128, 128 convolutions) is established as a benchmark without data augmentation.
2.  **Data Augmentation:** Apply preprocessing techniques like **rotate, flip, shear, or zoom** to existing training images using Keras utilities.
3.  **Model Training:** Train both the baseline and augmented models for 20 epochs and compare their performance, focusing on reduced overfitting.
4.  **Visualization:** Plot the training and validation loss and accuracy to visually confirm the benefit of augmentation.

---

## Dataset

The lab uses the **`cats_and_dogs_filtered`** dataset.

* **Download Source:** The dataset can be downloaded directly from the following Google Cloud Storage URL using `tf.keras.utils.get_file()`:
    ```
    [https://storage.googleapis.com/mledu-datasets/cats_and_dogs_filtered.zip](https://storage.googleapis.com/mledu-datasets/cats_and_dogs_filtered.zip)
    ```
    The notebook uses the following Python code snippet to download and extract the data:
    `path_to_zip = tf.keras.utils.get_file('cats_and_dogs.zip', origin=_URL, extract=True)`
* **Structure:** The data is organized into `train` (2000 files) and `validation` (1000 files) directories, with separate subdirectories for `cats` and `dogs`.
* **Preprocessing:** Images are loaded using `tf.keras.utils.image_dataset_from_directory`, resized to `(150, 150)`, and batched with a size of `20`.

---

## Technologies

* **TensorFlow/Keras:** Deep learning framework.
* **Matplotlib:** Data visualization.