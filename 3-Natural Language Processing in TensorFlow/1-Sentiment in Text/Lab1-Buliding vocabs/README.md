# 📓 Lab1: Building a Vocabulary

## 📝 Lab Goal

The primary goal of this lab is to introduce the process of preparing raw text data for a neural network in Natural Language Processing (NLP) tasks. Specifically, you will learn how to extract a unique vocabulary from a set of input texts (corpus) and assign a unique integer index to each word.

## 🛠️ Key Concepts & Tools

* **Corpus:** The input texts used to train the vocabulary.
* **Tokenization:** The process of breaking down sentences into individual words or units (tokens).
* **Vocabulary:** A set of all unique tokens extracted from the corpus.
* **TensorFlow API:**
    * **`tf.keras.layers.TextVectorization()`:** The core preprocessing layer used to handle text standardization, splitting, and token indexing.
    * **`.adapt(sentences)`:** The method used to analyze the input text (`sentences`) and build the vocabulary and indexing mapping.
    * **`.get_vocabulary()`:** The method used to retrieve the generated list of words and their corresponding integer indices.

## ⚙️ Step-by-Step Procedure

1.  **Initialize the Layer:** Create an instance of the `tf.keras.layers.TextVectorization()` layer.
2.  **Build the Vocabulary:** Call the `.adapt()` method on the layer, passing the sample sentences. This process automatically handles:
    * **Standardizing:** Lowercasing and stripping punctuation (default behavior).
    * **Splitting:** Breaking sentences into words.
    * **Indexing:** Assigning an integer index to each unique token, where more frequent words get lower indices.
3.  **Inspect the Vocabulary:** Retrieve the vocabulary list using `.get_vocabulary()`.

## ✨ Important Observations

* **Default Standardization:** The `TextVectorization` layer automatically lowercases words and removes punctuation (e.g., `'I, love my cat'` becomes three tokens: 'i', 'love', 'my', 'cat').
* **Index Ordering:** Words are indexed based on their frequency in the corpus (most frequent words get a lower index).
* **Special Tokens:** By default, the vocabulary reserves the first two indices:
    * Index **0:** Used for **padding**.
    * Index **1:** Used for **Out-of-Vocabulary (`[UNK]`)** tokens—words encountered later that were not in the original corpus.

---

**Next Steps:** The next lab will demonstrate how to use this generated vocabulary and the `TextVectorization` layer to convert raw input texts into the final integer sequences required for model training.next lab will demonstrate how to use this generated vocabulary and the `TextVectorization` layer to convert raw input texts into the final integer sequences required for model training.

