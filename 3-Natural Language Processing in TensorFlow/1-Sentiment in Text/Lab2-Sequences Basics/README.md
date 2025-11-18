# 📝 Generating Sequences and Padding

This notebook is focusing on the core steps of text data preparation for machine learning models: **converting text into numerical sequences** and ensuring **uniform size through padding and truncation**. It primarily uses the **`tf.keras.layers.TextVectorization`** layer and the **`tf.keras.utils.pad_sequences`** utility.

---

## 🚀 Key Objectives

The main goals of this lab are to demonstrate:

1.  **Vocabulary Creation:** Build a vocabulary from a small corpus of sample sentences using `TextVectorization.adapt()`.
2.  **Text to Sequence Conversion:** Convert individual strings and a list of strings into integer sequences based on the generated vocabulary.
3.  **Post-Padding:** Show the default **post-padding** behavior of the `TextVectorization` layer when applied to a list of strings, using `0` as the padding token.
4.  **Pre-Padding:** Use `tf.keras.utils.pad_sequences()` with `padding='pre'` (or default) to prepend padding zeros to sequences.
5.  **Padding and Truncation:** Demonstrate using `pad_sequences()` with the `maxlen` argument to limit sequence length and implicitly show the default **pre-truncation** (dropping tokens from the front).
6.  **Ragged Tensors:** Show how to use `TextVectorization(ragged=True)` to generate variable-length sequences (a **ragged tensor**) before applying `pad_sequences`.
7.  **Out-of-Vocabulary (OOV) Handling:** Illustrate how the special token index **`1`** (for `[UNK]`) is used for words not present in the vocabulary.

---

## 🛠️ Prerequisites

This notebook requires the following library:

* `tensorflow` (including `tf.keras.layers.TextVectorization` and `tf.keras.utils.pad_sequences`)

---

## 📖 Key Code Concepts

| Concept | Code Example | Description |
| :--- | :--- | :--- |
| **Vocabulary** | `vectorize_layer.get_vocabulary()` | Retrieves the vocabulary; token `0` is for padding, and token `1` is for OOV/`[UNK]`. |
| **Sequence Generation** | `vectorize_layer(sample_input)` | Converts a string or a list of strings into numerical sequences. |
| **Post-Padding** | `sequences_post = vectorize_layer(sentences)` | When passing a list, `TextVectorization` automatically **post-pads** the sequences to the length of the longest sequence. |
| **Pre-Padding** | `pad_sequences(sequences, padding='pre')` | Uses the utility function to explicitly add padding zeros to the **beginning** of the sequences. |
| **Truncation** | `pad_sequences(sequences, maxlen=5)` | Limits the length of the sequences, by default **truncating from the front** if the sequence is longer than `maxlen`. |
| **Ragged Tensor** | `TextVectorization(ragged=True)` | Prevents automatic padding, resulting in a variable-length tensor, which is useful before custom padding. |

---

## 💡 Special Tokens and Padding

* **Padding Token:** Index **`0`** is reserved for padding (zeroes).
* **OOV Token:** Index **`1`** is reserved for the `[UNK]` token, which is substituted for words not found in the learned vocabulary.

This lab provides the fundamental building blocks for preparing text data, which will be applied to a larger, real-world dataset in the next exercise.t found in the learned vocabulary.



This lab provides the fundamental building blocks for preparing text data, which will be applied to a larger, real-world dataset in the next exercise.

