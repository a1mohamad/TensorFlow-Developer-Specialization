# Sentiment Analysis with GloVe Embeddings

## 📄 Project Overview

This project is a required assignment (Week 3: Exploring Overfitting in NLP) focused on developing a **Sentiment Analysis** model. The core objective is to build a robust neural network architecture capable of classifying text sentiment (binary: negative/positive) while **actively exploring and mitigating overfitting**. The success of the project is measured by achieving strong generalization performance, which is typically observed through a stable or decreasing validation loss during training.

## 💻 Technical Details & Implementation

### Core Task
The task involves standard Natural Language Processing (NLP) processes for sequence data, including:
* **Data Pre-processing and Tokenization:** Converting raw text into a format suitable for the neural network.
* **Model Architecture:** Building a sequence model, with recommended layers such as `LSTM`, `GRU`, or `Conv` layers. The final architecture must include at least one `Dropout` layer to mitigate overfitting.

### Key Parameters
The model is configured with the following fixed parameters defined in the notebook:
* **Maximum Sequence Length (`MAX_LENGTH`):** 32
* **Embedding Dimension (`EMBEDDING_DIM`):** 100
* **Training Split (`TRAINING_SPLIT`):** 90% of the data
* **Batch Size (`BATCH_SIZE`):** 128

### Dataset

This project uses a cleaned variation of the **Sentiment140 dataset**.
* **Data Size:** 160,000 tweets (a subset of the original 1.6 million).
* **Classification:** Binary sentiment classification. The original labels are standardized to **0 (negative)** and **1 (positive)**.
* **Data Fields (per row):** target (sentiment), ids, date, flag, user, and text (the tweet content).

---

## 💾 GloVe Word Embeddings

This project relies on pre-trained **GloVe (Global Vectors for Word Representation)** vectors, instead of learning embeddings from scratch.

| Embedding Used | Source Corpus | Dimensions |
| :--- | :--- | :--- |
| **GloVe 6B.100d** | Wikipedia 2014 + Gigaword 5 | 100 dimensions |

The vectors are used to initialize the `tf.keras.layers.Embedding` layer with pre-trained weights that are set to be non-trainable, which leverages the pre-trained semantic knowledge.

#### ⬇️ Download GloVe 6B Embeddings

The required `glove.6B.100d.txt` file is contained within the full GloVe 6B download package.

**Direct Download Link (822 MB .zip file):**
[http://nlp.stanford.edu/data/glove.6B.zip](http://nlp.stanford.edu/data/glove.6B.zip)