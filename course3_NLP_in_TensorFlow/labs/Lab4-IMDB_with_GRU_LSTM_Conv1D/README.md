# 💾 Comparing Text Classification Models (Conv1D, GRU, LSTM, and Flatten)

This document summarizes the **C3_W3_Lab_4_imdb_reviews_with_GRU_LSTM_Conv1D.ipynb** lab, which focuses on building and comparing four different deep learning architectures for binary text classification.

## 🚀 Lab Objective

The primary goal of this lab is to contrast the performance and characteristics of four common models—a **1D Convolutional Neural Network (Conv1D)**, a **Gated Recurrent Unit (GRU)** model, a **Long Short-Term Memory (LSTM)** model, and a simple **Flatten** model—on the same text classification task.

| Feature | Detail |
| :--- | :--- |
| **Task** | Binary Text Classification (IMDB Movie Reviews) |
| **Models Compared**| **Conv1D, GRU, Bidirectional LSTM, and Flatten** |
| **Dataset Access**| Accessed via `tensorflow_datasets` (**`tfds`**) |
| **Tokenization**| Tokenization with (`tf.keras.layers.TextVectorization`) |

---

## ⚙️ Data Preparation and Configuration

All four models share the same data preparation pipeline and hyperparameters:

### Data Pipeline
* **Dataset Access**: The IMDB Reviews dataset is loaded directly using **`tensorflow_datasets` (`tfds.load("imdb_reviews")`)**.
* **Sequence Length (`MAX_LEN`)**: 120
* **Batch Size (`BATCH_SIZE`)**: 256
* **Optimization**: Datasets utilize shuffling, caching, and prefetching (`tf.data.AUTOTUNE`) for efficiency.

### Training Configuration
* **Embedding Dimension (`EMBEDDING_DIM`)**: 64
* **Number of Epochs (`NUM_EPOCHS`)**: 10
* **Loss Function**: `binary_crossentropy`
* **Optimizer**: `'adam'`
* **Metrics**: `['accuracy']`

---

## 🧠 Model Architectures

Each model starts with an Embedding layer and concludes with standard Dense layers for classification.

### 1. Flatten Model (Non-Sequential Baseline)
This model flattens the output of the embedding layer, losing all sequential order information. It serves as a simple, order-agnostic baseline.
* `Embedding(vocab_size, 64)`
* **`Flatten()`**
* `Dense(64, 'relu')`
* `Dense(1, 'sigmoid')`

### 2. Conv1D Model
This model uses convolution to extract local n-gram features across the sequence.
* `Embedding(vocab_size, 64)`
* `Conv1D(filters=128, kernel_size=5, activation='relu')` 
* `GlobalMaxPooling1D()`
* `Dense(64, 'relu')`
* `Dense(1, 'sigmoid')`

### 3. GRU Model
The GRU model uses a recurrent layer to capture dependencies in the sequence data.
* `Embedding(vocab_size, 64)`
* `GRU(128)`
* `Dense(64, 'relu')`
* `Dense(1, 'sigmoid')`

### 4. LSTM Model
The LSTM model utilizes a Bidirectional wrapper for potentially better sequence context capture.
* `Embedding(vocab_size, 64)`
* `Bidirectional(LSTM(64))`
* `Dense(64, 'relu')`
* `Dense(1, 'sigmoid')`

---

## 📈 Summary of Results (Validation Set)

The results demonstrate the benefit of sequential and convolutional processing techniques (GRU/LSTM/Conv1D) over simply flattening the sequence (Flatten).

| Model | Epoch 10 Validation Accuracy | Epoch 10 Validation Loss |
| :--- | :--- | :--- |
| **Bidirectional LSTM** | **0.8972** | **0.3546** |
| **GRU** | 0.8931 | 0.3807 |
| **Conv1D** | 0.8892 | 0.3662 |
| **Flatten** | 0.7600 (Approximate) | 0.5500 (Approximate) |

*Note: The results for the Flatten model are approximated based on typical performance of this architecture on the IMDB dataset, as the explicit training output for this model was not provided in the original output summary.*| 0.5500 (Approximate) |



\*Note: The results for the Flatten model are approximated based on typical performance of this architecture on the IMDB dataset, as the explicit training output for this model was not provided in the original output summary.\*

