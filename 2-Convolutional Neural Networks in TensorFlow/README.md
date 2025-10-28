# 📂 Course 2: Convolutional Neural Networks in TensorFlow

**Instructor:** Laurence Moroney

This repository contains the programming assignments, labs, and key concepts for **Course 2: Convolutional Neural Networks in TensorFlow**, part of the DeepLearning.AI TensorFlow Developer Specialization.

## 🚀 Course Goal

The primary goal of this course is to equip you with the knowledge and practical skills to build, train, and optimize **Convolutional Neural Networks (CNNs)** for **Computer Vision** tasks using **TensorFlow** and **Keras**. You'll move from simple neural networks to highly effective deep learning models for image classification.

---

## 📚 Course Outline

### Week 1: Exploring a Larger Dataset

* **Concepts:** Moving beyond simple datasets (like MNIST) to handle large, real-world image collections (e.g., **Cats vs. Dogs**).
* **Key Skills:** Using the `ImageDataGenerator` class to load, preprocess, and scale image data from directories.
* **Assignments/Labs:** Implementing and training a basic **Sequential CNN model** for binary classification on a large dataset.

### Week 2: Augmentation: A Technique to Avoid Overfitting

* **Concepts:** Understanding the problem of **overfitting** and effective **regularization** techniques.
* **Key Skills:** Implementing **Data Augmentation** (e.g., rotation, shifting, flipping) with `ImageDataGenerator` to artificially expand the training set. Applying **Dropout** layers for further regularization.
* **Assignments/Labs:** Modifying the CNN from Week 1 to include augmentation and dropout to significantly improve generalization and accuracy.

### Week 3: Transfer Learning

* **Concepts:** Introducing **Transfer Learning**—the practice of leveraging features learned by models trained on massive datasets (like ImageNet).
* **Key Skills:** Utilizing a pre-trained model (e.g., an Inception or VGG-style architecture) as a **feature extraction** base. **Freezing** the layers of the base model and adding custom output layers for a new task.
* **Assignments/Labs:** Building a highly accurate image classifier by applying Transfer Learning to a real-world problem.

### Week 4: Multiclass Classifications

* **Concepts:** Adapting CNN models for problems with **more than two classes** (multiclass classification).
* **Key Skills:** Correctly configuring the model's output layer (**softmax** activation) and the loss function (**sparse\_categorical\_crossentropy** or **categorical\_crossentropy**).
* **Assignments/Labs:** Developing a multiclass CNN model (e.g., on the **Rock-Paper-Scissors** dataset) and deploying all the learned techniques.

---

## 🛠 Required Tools & Setup

* **Python 3.x**
* **TensorFlow** and **Keras** (used via `tf.keras`)
* **Google Colab** or a similar environment (Jupyter Notebook) for running the exercises.
* The code is structured around the practical application of the Keras API.

---

## ✅ Best Practices Covered

* Handling data ingestion for images using `flow_from_directory`.
* Visualizing training metrics (loss and accuracy) to diagnose overfitting.
* Using callbacks to stop training early (**Early Stopping**).
* Understanding the trade-off between model complexity and generalization.from\\\_directory`.

\* Visualizing training metrics (loss and accuracy) to diagnose overfitting.

\* Using callbacks to stop training early (\*\*Early Stopping\*\*).

\* Understanding the trade-off between model complexity and generalization.

