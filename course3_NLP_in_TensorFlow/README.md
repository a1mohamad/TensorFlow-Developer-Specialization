# 📖 Natural Language Processing in TensorFlow (Course 3)

### DeepLearning.AI TensorFlow Developer Professional Certificate

## 📝 Course Overview

Welcome to **Course 3** of the TensorFlow Developer Professional Certificate Specialization, instructed by **Laurence Moroney**. This course dives into **Natural Language Processing (NLP)**, teaching you how to apply deep learning techniques to enable machines to understand and generate human language using the **TensorFlow** framework.

You will master the crucial steps of text preparation, utilize sophisticated sequence models, and build end-to-end NLP applications.

---

## 🎯 What You Will Learn

This course covers the foundational and intermediate NLP skills necessary for a developer role:

* **Tokenization and Text Preparation:** Convert raw text into numerical **tokens** and **sequences** suitable for neural network input.
* **Word Embeddings:** Understand the concept and implementation of **vector representations of words** (embeddings) to capture semantic relationships and context.
* **Sequence Models:** Implement advanced recurrent neural network architectures, including **LSTMs** (Long Short-Term Memory) and **GRUs** (Gated Recurrent Units), to handle sequential data.
* **Text Classification:** Build and train models for classic NLP tasks like **sentiment analysis** on large datasets.
* **Sequence Generation:** Apply LSTMs to a text corpus to train a model capable of **generating new, original text** (e.g., poetry).

---

## 🛠️ Technology Stack & Prerequisites

| Component | Detail |
| :--- | :--- |
| **Framework** | **TensorFlow 2.x** and the high-level **Keras API** |
| **Language** | **Python** |
| **Libraries** | `tensorflow`, `keras`, `numpy`, `matplotlib` |
| **Prerequisites** | Foundational knowledge of Python, basic machine learning concepts, and completion of Courses 1 & 2 (Convolutional Neural Networks). |

---

## 📅 Course Breakdown (Weekly Structure)

### Week 1: Sentiment in Text

* Introduction to NLP's "Hello World": text classification.
* Converting sentences to sequences using the **Tokenizer**.
* Using **padding** and handling **Out-of-Vocabulary (OOV)** tokens.
* Building a basic dense neural network for sentiment analysis.

### Week 2: Word Embeddings

* Deep dive into why embeddings are superior to one-hot encoding for text.
* Implementing the **`tf.keras.layers.Embedding`** layer.
* Improving the performance of classification models with embeddings.

### Week 3: Sequence Models

* Introduction to **Recurrent Neural Networks (RNNs)** for sequence processing.
* Implementing **LSTMs** and **GRUs** to remember long-term dependencies in text.
* Using **Bidirectional LSTMs** for richer feature extraction in classification tasks.

### Week 4: Sequence Models and Literature

* Advanced topic: **Text Generation**.
* Preprocessing text for a many-to-one word prediction task.
* Training an **LSTM model** to generate coherent new sequences of text.
* Understanding and using the **Categorical Cross-Entropy** loss function for word prediction.