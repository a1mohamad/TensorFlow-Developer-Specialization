# 📚 Training a binary classifier with the IMDB Reviews Dataset with Embedding

This notebook demonstrates the process of building and training a **binary sentiment classification model** using the Large Movie Review Dataset (IMDB Reviews), available through TensorFlow Datasets (TFDS). The final step includes extracting the trained word embeddings for visualization in the TensorFlow Embedding Projector.

---

## 📝 Lab Overview

The main objective of this lab is to:
1.  **Load and preprocess** the IMDB Reviews dataset for training.
2.  **Build** a simple sequential Keras model with an `Embedding` layer.
3.  **Train** the model to classify reviews as positive or negative.
4.  **Visualize** the trained word embeddings to observe word clustering.

---

## 💾 Dataset Information

The model is trained on the **IMDB Reviews** dataset, which is designed for binary sentiment classification.

* **Total Examples:** 100,000
* **Splits Used in Lab:**
    * **Train:** 25,000 labeled examples (reviews and sentiment labels).
    * **Test:** 25,000 labeled examples.
    * **Unsupervised:** 50,000 unlabeled examples (not used in this lab).
* **Label:** Binary (0 for negative, 1 for positive).

> ℹ️ **Note on Dataset Loading:**
>
> The notebook uses `tfds.load("imdb_reviews", ..., data_dir="./data/", download=False)` to load the dataset. This configuration is used in the lab to read from a pre-downloaded local copy.
>
> **If you run this notebook in a fresh environment without the data pre-downloaded, you should modify the loading cell to let TFDS handle the download:**
>
> ```python
> # Load the IMDB Reviews dataset, allowing TFDS to download if necessary
> imdb, info = tfds.load("imdb_reviews", with_info=True, as_supervised=True)
> ```

---

## 🧱 Model Architecture

The model is a simple sequential architecture designed for text classification:

1.  **`Embedding` Layer:** Maps word indices (from a vocabulary size of **10,000**) into a dense vector space (with an `EMBEDDING_DIM` of **16**). This layer learns a vector representation for each word.
2.  **`Flatten` Layer:** Flattens the 2D output of the `Embedding` layer into a 1D vector.
3.  **`Dense` Layer (Hidden):** A fully-connected layer with **6** neurons and a ReLU activation.
4.  **`Dense` Layer (Output):** A single-neuron output layer with a **sigmoid** activation function, suitable for binary classification.

The model is compiled with `loss='binary_crossentropy'`, `optimizer='adam'`, and `metrics=['accuracy']`.

---

## 📈 Training and Results (5 Epochs)

| Metric | Last Epoch (Epoch 5) | Observation |
| :--- | :--- | :--- |
| **Training Accuracy** | $\approx 99.86\%$ | High training accuracy. |
| **Validation Accuracy** | $\approx 80.23\%$ | Lower validation accuracy, indicating **overfitting** in this simple model architecture. |
| **Validation Loss** | $\approx 0.6905$ | Increasing validation loss suggests overfitting is occurring. |

---

## 🖼️ Word Embedding Visualization

The notebook extracts the learned weights from the `Embedding` layer and prepares two files for visualization:

* `vecs.tsv`: Contains the **16-dimensional vector weights** for each word.
* `meta.tsv`: Contains the corresponding **vocabulary words**.

These files can be uploaded to the [TensorFlow Embedding Projector](https://projector.tensorflow.org/) to visualize the word vectors. After uploading, you can observe how words with similar meanings or sentiments (e.g., *worst* vs. *fantastic*) are clustered together in the vector space. Projector](https://projector.tensorflow.org/) to visualize the word vectors. After uploading, you can observe how words with similar meanings or sentiments (e.g., \*worst\* vs. \*fantastic\*) are clustered together in the vector space.

