# 🤖 Sarcasm Classifier — Course 3 Assignment

This notebook implements a sarcasm detection pipeline focusing on **text preprocessing, vectorization, and non-RNN sequence models** . The architecture uses modern text vectorization and dense/convolutional approaches suitable for short text like headlines.

---

## 📝 Project Summary

- **Task:** Binary classification of news headlines (sarcasm vs non-sarcasm).
- **Focus:** Tokenization / text vectorization, embeddings or TF `TextVectorization`, and sequence processing without recurrent layers.
- **Note:** This README reflects the actual notebook contents (no LSTM/GRU/RNN used).


---

## 💾 What the Notebook Does

1. Loads and inspects the Sarcasm Headlines dataset.
2. Preprocesses text (cleaning, tokenization or `TextVectorization`).
3. Converts text to sequences or integer tokens and applies padding/truncation.
4. Builds a neural classifier using layers such as `Embedding`, `Conv1D`, `GlobalMaxPooling1D` / `GlobalAveragePooling1D`, and `Dense` (depending on the notebook).
5. Trains and evaluates the model, and reports accuracy / loss over epochs.


---

## 🧱 Model Summary (in-notebook)

Detected layers / components used in the notebook:

- `TextVectorization`
- `Embedding`
- `GlobalAveragePooling1D`
- `Dense`

**Model definition snippet (first occurrence):**

```python
def create_model():

    """

    Creates a text classifier model

    Returns:

      tf.keras Model: the text classifier model

    """

    # Define your model

    model = tf.keras.Sequential([ 

        tf.keras.Input(shape= (MAX_LENGTH,)),

        tf.keras.layers.Embedding(VOCAB_SIZE, EMBEDDING_DIM),

        tf.keras.layers.GlobalAveragePooling1D(),

        tf.keras.layers.Dense(10, activation= 'relu'),

        tf.keras.layers.Dense(5, activation= 'softmax')

    ])

    

    # Compile model. Set an appropriate loss, optimizer and metrics

    model.compile(

		loss= tf.keras.losses.SparseCategoricalCrossentropy(),

		optimizer= tf.keras.optimizers.Adam(learning_rate= 0.001),

		metrics=['accuracy'] 

	)



    return model
```


---

## 📈 Results & Notes

- Training/validation accuracy and loss are logged in the notebook. Inspect the training plots for performance and overfitting.
- For short texts like headlines, convolutional and embedding-based models can be effective and faster than RNNs.


---

## ⚙️ Requirements

- Python 3.8+
- TensorFlow
- NumPy
- (Optional) Jupyter / Colab


---
