#Image Data Preprocessing with a Validation Set

## **Overview**

This Jupyter Notebook, *C1\_W4\_Lab\_2\_image\_data\_preprocessing\_with\_validation.ipynb*, focuses on the **essential steps of preparing image data** for deep learning models. It implements the critical technique of setting aside a **validation set** to accurately measure a model's performance on data it has not been trained on.

---

## **Key Activities**

* **Data Partitioning:** Demonstrates how to split a loaded image dataset into two distinct groups: a **training set** and a **validation set**.
* **Model Generalization:** The primary objective is to use the validation set to **evaluate generalization**, enabling the user to monitor for **overfitting** during the training process.
* **Image Preparation:** Includes standard data preprocessing steps necessary for optimizing model training, such as **normalization** (scaling pixel values).
* **Feature Visualization:** Contains logic to visualize the outputs (activations) of various layers within the trained model, offering insight into how the network processes the image features.

---

## **Execution Workflow**

The notebook follows a logical flow designed for interactive analysis:

1.  **Setup & Load:** Imports necessary tools and loads the target image dataset.
2.  **Split Data:** Creates the separate Training and Validation data streams.
3.  **Train & Monitor:** Compiles and trains the neural network, explicitly using the validation set to track metrics (like loss and accuracy) per epoch.
4.  **Analyze:** Code for visualizing the model's intermediate feature maps.
5.  **Cleanup:** A final command is included to safely shut down the execution environment and free up resources.