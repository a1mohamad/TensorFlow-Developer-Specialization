## Week 3 - Lab 2: Exploring Convolutions

This document is the README for a lab that manually demonstrates the fundamental image processing operations of **convolution** and **max pooling**. These operations are the foundational building blocks of all Convolutional Neural Networks (CNNs).

***

### 🧱 Core Concepts: Manual Implementation

The lab focuses on implementing the following two operations on a 2D grayscale image using basic Python and NumPy:

1.  **Convolution:** Applying a small matrix (**filter** or **kernel**) across the image to transform it, typically used for **feature detection** (e.g., edges).
2.  **Max Pooling:** A downsampling technique that reduces the image size while retaining the most intense features.

***

### 💾 Image Loading and Preparation

The lab uses the built-in **`ascent`** image from the **SciPy** library.
* The image is loaded as a **NumPy array** and visualized using `matplotlib`.
* The code copies the original image array and retrieves its dimensions ($X$ and $Y$).

***

### 1. Manual Convolution

This step applies a $3 \times 3$ filter (kernel) across the image.

#### Filter (Kernel)
A $3 \times 3$ matrix is defined (e.g., an edge-detection filter). The code explicitly iterates through the image pixels, multiplying each $3 \times 3$ neighborhood by the filter values and summing the result to calculate the new pixel value.

The output is a **transformed image** where features highlighted by the filter (like edges) are enhanced. The resulting pixel values are clipped to the $0-255$ range.

***

### 2. Effect of Max Pooling

This step demonstrates $2 \times 2$ Max Pooling, which is designed to compress the image while preserving detected features.

#### Process
1.  **Image Reduction:** A new image is created with dimensions halved ($\frac{1}{4}$ the size of the transformed image).
2.  **Downsampling:** The code iterates over the transformed image in $2 \times 2$ blocks.
3.  **Maximum Value Selection:** From each $2 \times 2$ block, the single **largest pixel value** is selected and placed into the corresponding pixel of the new, smaller image.

The final visualization shows the **compressed image**, demonstrating that the important features highlighted by the convolution are maintained despite the significant reduction in size.