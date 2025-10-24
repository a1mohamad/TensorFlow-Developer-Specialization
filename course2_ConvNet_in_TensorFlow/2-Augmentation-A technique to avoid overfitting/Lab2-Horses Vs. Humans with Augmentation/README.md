\# Data Augmentation on the Horses or Humans Dataset



---



\## 💡 Overview



This project is based on an ungraded lab focusing on \*\*data augmentation\*\* techniques applied to a Convolutional Neural Network (CNN) for the \*\*Horses or Humans\*\* binary classification task. The goal is to improve model generalization and mitigate \*\*overfitting\*\* by synthetically expanding the training dataset.



---



\## 🐴 Dataset Access



The dataset used, \*\*Horses or Humans\*\*, is a standard collection of images.



\* \*\*Public Access:\*\* You can easily access this dataset using the \*\*TensorFlow Datasets (TFDS)\*\* catalog:

    \* `tfds.image\\\_classification.HorsesOrHumans`

\* \*\*Size:\*\*

    \* Training Set: 1027 images

    \* Validation Set: 256 images

\* \*\*Classes:\*\* Horses (0) and Humans (1).

\* \*\*Image Size:\*\* All images are processed to \*\*(300, 300)\*\* pixels.



\*\*\*



\### ⚠️ Limitation



The original image files and directory structure (`horse-or-human/train/...` etc.) necessary to run the notebook were \*\*not uploaded\*\* for this repository. You must download the dataset separately if you intend to execute the code.



---



\## 🖼️ Data Augmentation Pipeline



A sequential model layer is used to apply on-the-fly transformations to the training images, ensuring the model sees a slightly different version of each image in every epoch.



The key transformations applied are:



\* \*\*RandomFlip:\*\* Horizontal flipping.

\* \*\*RandomRotation:\*\* Random rotation up to 20% (0.2) of the full circle.

\* \*\*RandomTranslation:\*\* Random horizontal and vertical translation up to 20% (0.2) of the image height/width.

\* \*\*RandomZoom:\*\* Random zoom up to 20% (0.2).



---



\## 🧠 Model Architecture



The CNN is designed as a deep, sequential network:



1\.  \*\*Preprocessing:\*\* Input layer followed by a `Rescaling(1./255)` layer.

2\.  \*\*Feature Extraction:\*\* Five blocks of \*\*`Conv2D`\*\* (with ReLU activation) followed by \*\*`MaxPooling2D`\*\* (2, 2). The filter count progresses from 16 up to 64.

3\.  \*\*Classification:\*\* A `Flatten` layer connects the convolutional base to the dense layers, which include a 512-neuron hidden layer (`'relu'`) and a final single-neuron output layer (`'sigmoid'`) for binary classification.



---



\## 🛠️ Requirements



The notebook requires the following core libraries:



\* \*\*`tensorflow`\*\*

\* \*\*`matplotlib.pyplot`\*\*

\* `os`

