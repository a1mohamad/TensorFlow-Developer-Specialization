## Week 3 - Assignment: Improve MNIST with Convolutions

This document is the README for the Week 3 assignment focused on improving the classification accuracy of the **MNIST handwritten digit dataset** by integrating a basic Convolutional Neural Network (CNN) architecture.

The goal is to achieve an accuracy of **99.5% or greater** in **under 10 epochs** using a model that adds only a single $\text{Conv2D}$ layer and a single $\text{MaxPooling2D}$ layer to a standard dense network.

***

### 🎯 Assignment Requirements

1.  **Architecture:** The model must include **exactly one $\text{Conv2D}$ layer** and **exactly one $\text{MaxPooling2D}$ layer**.
2.  **Performance:** Achieve $\geq 99.5\%$ accuracy.
3.  **Efficiency:** Succeed in **less than 10 epochs**.
4.  **Early Stopping:** Implement a custom $\text{Callback}$ to stop training when $99.5\%$ accuracy is reached and print the string: `"Reached 99.5% accuracy so cancelling training!"`.

***

### 💾 Data Loading and Pre-processing

The assignment uses the **MNIST** training set.

#### Exercise 1: $\text{reshape\_and\_normalize}$

This function prepares the image data for the CNN.

1.  **Reshape:** The images must be reshaped to include an extra dimension for the color channel: $(60000, 28, 28, 1)$.
2.  **Normalize:** Pixel values are normalized from the $0-255$ range to $0-1$ by dividing by $255.0$.

***

### 🛑 Early Stopping Implementation

#### Exercise 2: $\text{EarlyStoppingCallback}$

A custom $\text{tf.keras.callbacks.Callback}$ class is defined to handle the early stopping requirement. The $\text{on\_epoch\_end}$ method checks the training accuracy at the end of each epoch. If the `accuracy >= 0.995`, the training is stopped, and the required success message is printed.

***

### 🧠 Model Architecture

#### Exercise 3: $\text{convolutional\_model}$

This function returns the compiled CNN model.

**Model Structure** (Must include one $\text{Conv2D}$ and one $\text{MaxPooling2D}$ layer):
1.  $\text{Input}$ layer (shape: $(28, 28, 1)$).
2.  $\text{Conv2D}$ layer (Feature extraction).
3.  $\text{MaxPooling2D}$ layer (Downsampling).
4.  $\text{Flatten}$ layer.
5.  $\text{Dense}$ hidden layers (Classification).
6.  $\text{Dense}$ output layer (10 units, $\text{Softmax}$).

The model must be compiled using the $\text{Adam}$ optimizer and $\text{sparse\_categorical\_crossentropy}$ loss.xt{Dense}$ output layer (10 units, $\\text{Softmax}$).



The model must be compiled using the $\\text{Adam}$ optimizer and $\\text{sparse\\\_categorical\\\_crossentropy}$ loss.

