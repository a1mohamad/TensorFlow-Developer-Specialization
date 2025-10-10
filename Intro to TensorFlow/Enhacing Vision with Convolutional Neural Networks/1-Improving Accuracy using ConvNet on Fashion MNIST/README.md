## Week 2 - Lab 1: Computer Vision Accuracy with Convolutions

This document is a README file for the lab exploring how **Convolutional Neural Networks (CNNs)** improve image classification accuracy over **Shallow Neural Networks (SNNs)** using the **Fashion MNIST** dataset.

***

### 💾 Data and Preprocessing

The **Fashion MNIST** dataset ($70,000$ images, $28 \times 28$ pixels) is used. The data is loaded using `tf.keras.datasets.fashion_mnist` and normalized by dividing the pixel values by $255.0$.

***

### 1. Shallow Neural Network (SNN) Baseline

This model establishes a baseline performance, typically achieving an accuracy of $\sim 87-89\%$.

#### SNN Architecture
The simple SNN consists of:
* An **Input Layer** ($28 \times 28 \times 1$).
* A **Flatten** layer to convert the 2D image data into a 1D vector.
* A **Dense** hidden layer (128 neurons) with $\text{ReLU}$ activation.
* A final **Dense** output layer (10 neurons) with $\text{Softmax}$ activation for classification.

***

### 2. Convolutional Neural Network (CNN) Improvement

Introducing **Conv2D** and **MaxPool2D** layers significantly boosts accuracy (expected $\sim 90-92\%+$) by focusing on image features like edges and patterns.

#### CNN Architecture
The CNN adds a feature-extraction block before the dense layers:
* **Input Layer** ($28 \times 28 \times 1$).
* **Conv2D** layer (64 filters, $3\times3$ kernel, $\text{ReLU}$): Applies filters to detect features.
* **MaxPooling2D** layer ($2\times2$ pool size): Downsamples the feature map, reducing dimensionality.
* **Flatten** layer.
* **Dense** hidden layer (128 neurons, $\text{ReLU}$).
* **Dense** output layer (10 neurons, $\text{Softmax}$).

#### Early Stopping Callback
A custom **Callback** is used during training to automatically stop the process if the training accuracy reaches $\geq 93\%$, which helps prevent **overfitting**.

***

### 🔬 Visualization and Exercises

#### Visualizing Activations
The lab includes code to visualize the **feature maps** output by the $\text{Conv2D}$ and $\text{MaxPooling2D}$ layers. This allows inspection of how the network transforms the raw image into essential, highlighted features.

#### Exercises for Experimentation
1.  **Filter Count:** Change the number of filters (e.g., 64 to 16 or 32) and note the impact on training time and accuracy.
2.  **Removing Layers:** Remove the $\text{Conv2D}$ and $\text{MaxPooling2D}$ block entirely.
3.  **Adding Layers:** Add more $\text{Conv2D}$ and $\text{MaxPooling2D}$ blocks and observe potential for **overfitting**.
4.  **Single Conv-Pool Block:** Retain only the first $\text{Conv2D}$ and $\text{MaxPooling2D}$ block.
5.  **Loss Callback:** Modify the custom callback to stop training based on a threshold for the **loss function** instead of accuracy.