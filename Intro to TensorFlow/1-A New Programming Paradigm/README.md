# Hello World of Deep Learning 🤖

This lab shows the simplest way to train a **Neural Network** using **TensorFlow/Keras** to learn a simple rule: **$y = 2x - 1$**.

---

## 💡 The Idea

We give the network a few $\mathbf{x}$ and $\mathbf{y}$ pairs (data) and let it figure out the math, rather than programming the formula ourselves.

---

## 🛠️ Key Steps

### 1. Setup
We import **TensorFlow** (with Keras) and **NumPy** for handling the data.

### 2. The Data
We create 6 pairs where the $\mathbf{y}$ value is always $(2 * \mathbf{x}) - 1$.

| $\mathbf{x}$ | $\mathbf{y}$ |
| :---: | :---: |
| -1.0 | -3.0 |
| ... | ... |
| 4.0 | 7.0 |

### 3. Build the Model
We create the smallest network possible:
* A **Sequential** model.
* **1 Layer** (`Dense`).
* **1 Neuron** (`units=1`).

### 4. Training

We **compile** the model with:
* **Loss**: `mean_squared_error` (to measure errors).
* **Optimizer**: `sgd` (to adjust the neuron's weights).

Then, we call **`model.fit()`** for 500 **epochs**. The network iteratively guesses, checks its error, and corrects itself.

### 5. Prediction

After training, the network can predict the output for a new input, like $x=10$.

```python
# The prediction should be very close to 19.
model.predict(np.array([10.0]))
```

The result is an approximation (e.g., 18.999...) because the network learned from limited data, reflecting how real-world neural networks work with probabilities.