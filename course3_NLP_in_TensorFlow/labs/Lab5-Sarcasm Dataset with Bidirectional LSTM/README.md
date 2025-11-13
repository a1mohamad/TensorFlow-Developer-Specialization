# Sarcasm Detection Model using Bidirectional LSTMs

This repository contains an Ungraded Lab demonstrating how to train a Sarcasm Detection Model using a Bidirectional LSTM (Bi-LSTM).

## Project Goal
The primary objective of this lab is to revisit the News Headlines Dataset for Sarcasm Detection and use a Bi-LSTM model architecture for binary classification (sarcastic vs. non-sarcastic).

## Dataset
* **Name:** [News Headlines Dataset for Sarcasm Detection](https://www.kaggle.com/datasets/rmisra/news-headlines-dataset-for-sarcasm-detection)
* **File:** `sarcasm.json`
* **Split:** The dataset is split into 20,000 examples for training and the remainder for testing.

## Model Architecture and Training Parameters

The model is a sequential Keras model with the following layers and key hyperparameters:

### Model Architecture
1.  **Embedding Layer:** Maps words from the vocabulary to a dense vector space.
2.  **Bidirectional LSTM Layer:** A recurrent layer that processes the sequence input in both forward and backward directions to capture context more effectively.
3.  **Dense Layer (ReLU):** A standard dense layer for non-linear transformation.
4.  **Dense Layer (Sigmoid):** The output layer for binary classification.

### Hyperparameters
* **Vocabulary Size (`VOCAB_SIZE`):** 10,000
* **Max Sequence Length (`MAX_LENGTH`):** 32
* **Embedding Dimension (`EMBEDDING_DIM`):** 16
* **LSTM Dimension (`LSTM_DIM`):** 32
* **Number of Epochs (`NUM_EPOCHS`):** 10

### Model Summary
| Layer (type) | Output Shape | Param # |
| :--- | :--- | :--- |
| embedding_10 (Embedding) | (None, 32, 16) | 160,000 |
| bidirectional_10 (Bidirectional) | (None, 64) | 12,544 |
| dense_20 (Dense) | (None, 24) | 1,560 |
| dense_21 (Dense) | (None, 1) | 25 |
| **Total params:** | | **174,129** |
| **Trainable params:** | | **174,129** |
*Summary extracted from the notebook's output.*

## Training Results
The model was trained for 10 epochs using the Adam optimizer and binary crossentropy loss.

| Metric | Training Result (Epoch 10) | Validation Result (Epoch 10) |
| :--- | :--- | :--- |
| **Accuracy** | 0.9954 | 0.8275 |
| **Loss** | 0.0156 | 1.1930 |
*Results extracted from the notebook's training output.*

The results show significant overfitting, with very high training accuracy and a large divergence between training and validation loss.ining output.\*



The results show significant overfitting, with very high training accuracy and a large divergence between training and validation loss.

