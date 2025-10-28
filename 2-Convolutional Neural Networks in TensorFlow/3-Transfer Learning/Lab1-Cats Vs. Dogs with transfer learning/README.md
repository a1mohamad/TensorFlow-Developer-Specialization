# Transfer Learning with InceptionV3

This notebook contains an ungraded lab notebook (`C2_W3_Lab_1_transfer_learning.ipynb`) demonstrating the principles of **Transfer Learning** in deep neural networks.

The primary goal of this lab is to achieve good performance on a small dataset by leveraging the features learned by a large, pre-trained model, thereby saving significant training time.

## Objective

The core objective is to practice the key steps of transfer learning:

1.  Use a pre-trained base model's convolutional layers as a fixed feature extractor.
2.  Attach new, trainable dense layers to the end of the feature extractor.
3.  Train only the new dense network to adapt the pre-trained features to a new, specific task.

## Methodology and Implementation

The lab uses the **InceptionV3** architecture from `tf.keras.applications` as the base model.

### Key Steps:

* **Model Initialization**: The InceptionV3 model is initialized with the ImageNet weights, excluding the original top fully-connected layer (`include_top=False`).
* **Input Shape**: The input shape for the model is configured to be **(150, 150, 3)**.
* **Layer Freezing (Feature Extraction)**: The weights of the entire pre-trained InceptionV3 model are **frozen** by setting `layer.trainable = False`.
* **Feature Truncation**: The feature extractor is intentionally limited to the output of the **`mixed7`** layer, as these intermediate features are considered more generalized and less specialized than the very last layers.
* **Custom Head**: A new classification head consisting of fully-connected (dense) layers is added on top of the `mixed7` output.

## Prerequisites

To run this notebook, you will need the following Python libraries:

* `tensorflow`
* `matplotlib`
* The pre-trained **InceptionV3 weights** file, which can be downloaded from: [InceptionV3 weights file](https://storage.googleapis.com/mledu-datasets/inception_v3_weights_tf_dim_ordering_tf_kernels_notop.h5).//storage.googleapis.com/mledu-datasets/inception\_v3\_weights\_tf\_dim\_ordering\_tf\_kernels\_notop.h5).

