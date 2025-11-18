# Multiple LSTMs for Sentiment Classification

## Overview

This notebook contains an ungraded lab demonstrating how to build a deep learning model for sentiment classification using **multiple stacked Long Short-Term Memory (LSTM) layers**.

The key focus is on the architecture required to stack multiple recurrent layers, specifically enabling the `return_sequences=True` flag for intermediate LSTM layers to ensure the output sequence can be consumed by the next layer.

***

## Dataset

* **Dataset:** IMDB Reviews Dataset (`imdb_reviews`).
* **Access Method:** The dataset is accessed directly using **`tensorflow_datasets` (tfds)**.
* **Task:** Binary Sentiment Classification (positive/negative movie review).

***

## Model Architecture

The model uses a stacked sequence of layers, primarily featuring two bidirectional LSTM layers for enhanced feature extraction from the text sequence.

| Layer Type | Output Shape | Description |
| :--- | :--- | :--- |
| `Embedding` | (None, None, 64) | Converts tokenized integer sequences into dense vectors. |
| `Bidirectional(LSTM(32, return_sequences=True))` | (None, None, 64) | The first LSTM layer wrapped in a Bidirectional layer. **`return_sequences=True` is crucial for feeding the entire output sequence to the next LSTM**. |
| `Bidirectional(LSTM(16))` | (None, 32) | The second LSTM layer. `return_sequences=False` (default) is used as it's the final recurrent layer before the dense layers. |
| `Dense(64, activation='relu')` | (None, 64) | Standard dense layer with ReLU activation. |
| `Dense(1, activation='sigmoid')` | (None, 1) | Output layer for binary classification. |

**Total Parameters:** 526,017.

***

## Data Preparation Summary

1.  The IMDB reviews dataset is loaded using **`tfds.load("imdb_reviews")`**.
2.  A pre-trained subword vocabulary is loaded, and a `keras_nlp.tokenizers.WordPieceTokenizer` is initialized.
3.  A custom `padding_func` is applied to ensure all sequences have a uniform length after tokenization, using 'pre' padding and 'post' truncation.
4.  The final `tf.data.Dataset` is optimized using `shuffle`, `cache`, `prefetch`, and `batch` (with `BATCH_SIZE = 256`) for efficient training.

***

## Training Configuration

* **Loss Function:** `'binary_crossentropy'`.
* **Optimizer:** `'adam'`.
* **Metrics:** `'accuracy'`.
* **Epochs (Example Run):** 5.

The notebook notes that the addition of another LSTM layer increases the training time and that the model may start to overfit quickly.

The notebook notes that the addition of another LSTM layer increases the training time and that the model may start to overfit quickly.

