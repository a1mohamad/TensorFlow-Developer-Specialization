# 💾 Text Classification with 1D Convolutional Neural Networks (Conv1D)

This file summarizes the contents and results of the ungraded lab **C3_W3_Lab_3_Conv1D.ipynb**, which demonstrates the use of a **1D Convolutional Neural Network (Conv1D)** for a binary text classification task.

## 🚀 Project Overview

The primary goal of this lab is to build and train a deep learning model to classify movie reviews as either **Positive** or **Negative** using a `Conv1D` layer. This model architecture is powerful for extracting key n-gram and sequential features from text.

| Feature | Detail |
| :--- | :--- |
| **Goal** | Binary Text Classification (Positive/Negative review) |
| **Core Layer**| `tf.keras.layers.Conv1D` |
| **Dataset**| IMDB Movie Reviews (from `tensorflow_datasets`) |
| **Tokenization**| Subword Tokenization using `keras_nlp.tokenizers.WordPieceTokenizer` |
| **Data Length**| Sequences are padded to a fixed length of 256. |

---

## 🧠 Model Architecture

The model is a sequential Keras model built specifically for processing the embedded sequence data.

| Layer (Type) | Output Shape | Parameters | Purpose |
| :--- | :--- | :--- | :--- |
| `Input` | `(None,)` | 0 | Placeholder for tokenized sequences. |
| `Embedding` | `(None, None, 64)` | 488,640 | Converts integer tokens into **dense 64-dimensional vectors**. |
| `Conv1D` | `(None, None, 128)` | 41,088 | Applies 128 filters of size **5** across the sequence dimension to learn local patterns.  |
| `GlobalMaxPooling1D`| `(None, 128)` | 0 | Aggregates the feature maps by taking the maximum value, resulting in a fixed-length vector regardless of input sequence length. |
| `Dense` | `(None, 64)` | 8,256 | Intermediate dense layer with **ReLU** activation. |
| `Dense` | `(None, 1)` | 65 | Output layer with **Sigmoid** activation for the final binary prediction. |

**Total Trainable Parameters:** 538,049

---

## ⚙️ Configuration and Training

The model was compiled and trained using standard settings for binary classification.

### Training Parameters

| Parameter | Value |
| :--- | :--- |
| **Loss Function** | `'binary_crossentropy'` |
| **Optimizer** | `'adam'` |
| **Metrics** | `['accuracy']` |
| **Epochs** | 10 |
| **Batch Size** | 256 |

### Data Pipeline Optimization

The dataset pipeline was optimized for performance using `tf.data.Dataset`:

* **Tokenization and Padding:** Sequences are tokenized, then padded (`padding='pre'`) and truncated (`truncating='post'`) to a fixed length of 256.
* **Caching:** The dataset is cached (`.cache()`) after the initial loading and preprocessing to prevent re-reading the data from disk in subsequent epochs.
* **Prefetching:** Data loading and preprocessing are decoupled from training using `.prefetch(tf.data.AUTOTUNE)`.

---

## 📊 Results

The model was trained for 10 epochs. The results demonstrate the Conv1D layer's effectiveness at feature extraction for text data.

| Metric | Final Training Value | Final Validation Value |
| :--- | :--- | :--- |
| **Accuracy** | $\approx 99.99\%$ | $\approx 89.56\%$ |
| **Loss** | $\approx 0.0023$ | $\approx 0.3630$ |

The high training accuracy suggests the model learned the training data well, while the validation accuracy around 90% indicates strong generalization capability, although the gap suggests some **overfitting**.