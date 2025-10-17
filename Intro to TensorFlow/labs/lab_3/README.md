# Effect of Compacted Images in Training 📉

This notebook, `C1_W4_Lab_3_compacted_images.ipynb`, demonstrates the practical effects of **reducing image resolution** on a Convolutional Neural Network (CNN) model's architecture, training speed, and performance.

The core idea is to show that image compaction can be a valuable technique for **speeding up training** and **saving compute resources** during the exploratory phase of a deep learning project.

***

## Key Features & Differences

| Feature | Details |
| :--- | :--- |
| **Dataset** | Horse or Human classification (Binary Classification). |
| **Image Compaction** | The model uses **150x150** images instead of the typical 300x300. |
| **Model Architecture** | A standard sequential CNN with 3 Conv/MaxPool blocks, a Flatten layer, and a Dense layer for binary output. **The `input_shape` is explicitly set to (150, 150, 3).** |
| **Data Preprocessing**| The `tf.keras.utils.image_dataset_from_directory` utility is used, with `image_size=(150, 150)` specified to handle the compaction. Images are then rescaled to the $[0, 1]$ range. |
| **Objective** | Observe the trade-off: **Does the smaller input size lead to significantly faster training without a major drop in accuracy?** |

***

## Model Architecture Summary

The model is defined using Keras Sequential API. Note how the reduced input size affects the output shapes of the convolutional layers, leading to fewer parameters in the final Dense layers compared to a 300x300 model.

| Layer (Type) | Output Shape | Parameters |
| :--- | :--- | :--- |
| **InputLayer** | (150, 150, 3) | 0 |
| **Conv2D (1)** | (148, 148, 16) | 448 |
| **MaxPooling2D (1)** | (74, 74, 16) | 0 |
| **Conv2D (2)** | (72, 72, 32) | 4,640 |
| **MaxPooling2D (2)** | (36, 36, 32) | 0 |
| **Conv2D (3)** | (34, 34, 64) | 18,496 |
| **MaxPooling2D (3)** | (17, 17, 64) | 0 |
| **Flatten** | (18496) | 0 |
| **Dense (Hidden)** | (512) | 9,470,464 |
| **Dense (Output)** | (1) | 513 |

**Total Trainable Parameters:** $\approx 9.49$ Million

***

## Experimentation Notes

The notebook encourages the user to:

1.  **Observe Training Speed:** Note the time-per-epoch compared to models using larger images. Training is expected to be faster due to smaller input tensors.
2.  **Analyze Accuracy:** Compare the final training and validation accuracies to see the performance impact of using lower resolution data.
3.  **Visualize Features:** Observe the intermediate feature maps. The output from the last `MaxPooling2D` layer will be **17x17x64**, visually confirming the reduced information flow (more abstract representations) compared to a larger input size.

This exercise is a practical demonstration of **early-stage model optimization** by adjusting the image data pipeline.