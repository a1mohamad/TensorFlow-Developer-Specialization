# 📝 Text preprocessing on Sarcasm

## Tokenizing the Sarcasm Dataset

This notebook is designed to introduce the **preprocessing steps** for the **News Headlines Dataset for Sarcasm Detection**. It demonstrates how to load the dataset, extract the text data (headlines), and use **TensorFlow's `TextVectorization` layer** and **`pad_sequences` utility** to convert the text into numerical, padded sequences for use in machine learning models.

---

## 🚀 Key Objectives

The main goals of this lab are:

1.  **Download and Inspect the Dataset:** Load the `sarcasm.json` file, which contains news headlines and an `is_sarcastic` label.
2.  **Preprocessing with Post-Padding:** Use `tf.keras.layers.TextVectorization` to build a vocabulary and generate **post-padded sequences** (where padding zeros are appended to the end).
3.  **Preprocessing with Pre-Padding:** Demonstrate an alternative approach using `TextVectorization(ragged=True)` to generate variable-length sequences, followed by `tf.keras.utils.pad_sequences()` to create **pre-padded sequences** (where padding zeros are prepended to the beginning).
4.  **Compare Results:** Inspect the final dimensions of the padded sequences (e.g., **(26709, 39)**) and observe the difference in padding location for a sample headline.

---

## 🛠️ Prerequisites

This notebook requires the following libraries:

* `tensorflow` (including `tf.keras.layers.TextVectorization`)
* `json`
* `tensorflow_datasets`
* `tensorflow.keras.utils.pad_sequences`

---

## 📖 Key Code Concepts

| Concept | Description |
| :--- | :--- |
| **Data Loading** | Python's `json` module is used to load the dataset from the downloaded file `sarcasm.json`. |
| **Vocabulary Building** | The `vectorize_layer.adapt(sentences)` method scans the entire set of headlines to create a vocabulary mapping words to unique integer IDs. |
| **Post-Padding (Default)** | The default behavior of `TextVectorization` (when not using `ragged=True`) is to pad sequences to the length of the longest input sequence by appending zeros. |
| **Pre-Padding (Custom)** | Achieved by setting `TextVectorization(ragged=True)` to get variable-length sequences, then explicitly calling `pad_sequences(..., padding='pre')` on the resulting NumPy array. |

---

## 💡 Output Observation

The notebook demonstrates that for the sample headline:
`mom starting to fear son's web series closest thing she will have to grandchild`

* **Post-padded sequences** show the padding zeros at the **end** of the sequence.
* **Pre-padded sequences** show the padding zeros at the **beginning** of the sequence.