# 🧠 Sentiment Classification with LSTM

This project implements a **single-layer LSTM** model to perform **sentiment analysis** on the **IMDB movie reviews dataset** using **TensorFlow** and **Keras**.  
It’s part of the **TensorFlow Developer Specialization (Course 3 – NLP)** and focuses on understanding sequential data and text representation.

---

### 📊 Dataset
The **IMDB Reviews Dataset** contains 50,000 movie reviews labeled as positive or negative.  
You can easily load and download it using **TensorFlow Datasets (TFDS)**:

```python
import tensorflow_datasets as tfds
imdb, info = tfds.load('imdb_reviews', with_info=True, as_supervised=True)
```
📌 The **IMDB Subword Tokenization** dataset version is also uploaded for exploring subword-based text encoding.

---

### 🧩 What’s Inside
- Preprocessing and tokenizing text data  
- Embedding layers for representing words  
- Building and training a **single-layer LSTM** model  
- Evaluating performance on the IMDB dataset  

---

### 🛠️ Libraries Used
- TensorFlow / Keras  
- TensorFlow Datasets (TFDS)  
- NumPy  

braries Used

\- TensorFlow / Keras  

\- TensorFlow Datasets (TFDS)  

\- NumPy  





