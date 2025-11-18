# 🤖 Building a Sarcasm Classifier with LSTM and Embeddings

This notebook demonstrates the process of building and training a **sarcasm detection model** using a dataset of news headlines.  
The task focuses on natural language preprocessing and sequence modeling with TensorFlow.

---

## 📝 Lab Overview

The main objectives of this project are to:
1. **Load and preprocess** text data for sarcasm detection.
2. **Tokenize and pad** sequences to prepare inputs for a neural network.
3. **Use word embeddings** to represent textual data in dense vector form.
4. **Build and train** an LSTM-based model to classify sarcastic vs. non-sarcastic headlines.

---

## 💾 Dataset Information

The model is trained on a **Sarcasm Headlines Dataset**, which contains labeled news headlines indicating whether each is sarcastic or not.

* **Input:** News headline text.  
* **Label:** Binary (1 = sarcastic, 0 = non-sarcastic).  
* **Goal:** Predict sarcasm from text using learned word embeddings.

---

## 🧱 Model Architecture

The model follows a sequential structure designed for text classification:

1. **`Embedding` Layer:** Converts word indices to dense vector embeddings.  
2. **`LSTM` Layer:** Captures sequential context and word dependencies.  
3. **`Dense` Layers:** Fully connected layers for feature extraction.  
4. **`Output` Layer:** Single neuron with sigmoid activation for binary classification.

Compiled with `binary_crossentropy` loss, `adam` optimizer, and `accuracy` metric.

---

## 📈 Training and Results

| Metric | Observation |
| :--- | :--- |
| **Training Accuracy** | High convergence after several epochs. |
| **Validation Accuracy** | Stable, with slight overfitting due to dataset size. |

The model successfully learns patterns of sarcasm from word usage and structure.

---

## 🧩 Key Learnings

- Importance of tokenization and padding in text pipelines.  
- How embeddings help models understand semantics.  
- Using LSTM layers to capture contextual relationships in text.

---

## ⚙️ Technologies Used

- TensorFlow / Keras  
- Python  
- NumPy  
- NLP Preprocessing

---e contextual relationships in text.



---



\## ⚙️ Technologies Used



\- TensorFlow / Keras  

\- Python  

\- NumPy  

\- NLP Preprocessing



---

