\# README: Week 1 Assignment - House Price Prediction 🏘️



This repository contains the solution for the Week 1 Assignment of the TensorFlow Developer Specialization. The goal is to build and train a \*\*simple neural network\*\* to predict house prices based on the number of bedrooms, following a fixed formula.



---



\## 💡 The Problem



The house price model is defined by this simple linear rule:

$$\\text{Price} = 50k + (\\text{Number of Bedrooms} \\times 50k)$$



\* 1 bedroom house: $50k + 50k = 100k$

\* 2 bedroom house: $50k + 100k = 150k$

\* ...and so on.



The task is to train a model to predict the price for a 7-bedroom house (expected price: $400k$).



---



\## 🔑 Scaling and Data



The hint suggests \*\*scaling\*\* the prices to make training easier and faster.

\* \*\*Features ($\\mathbf{x}$)\*\*: Number of bedrooms (e.g., 1.0, 2.0, 3.0...).

\* \*\*Targets ($\\mathbf{y}$)\*\*: Price in \*\*hundreds of thousands of dollars\*\* (e.g., $100k \\rightarrow 1.0$, $150k \\rightarrow 1.5$, $400k \\rightarrow 4.0$).



This changes the relationship the network must learn to:

$$\\text{Scaled Price} = 0.5 + (\\text{Number of Bedrooms} \\times 0.5)$$



\### Exercise 1: `create\\\_training\\\_data`



Creates the training data (6 points, from 1 to 6 bedrooms) as NumPy arrays of floats.



| Bedrooms ($\\mathbf{x}$) | Price (Hundreds of K - $\\mathbf{y}$) |

| :---: | :---: |

| 1.0 | 1.0 |

| 2.0 | 1.5 |

| 3.0 | 2.0 |

| 4.0 | 2.5 |

| 5.0 | 3.0 |

| 6.0 | 3.5 |



---



\## 🏗️ Model Architecture and Training



\### Exercise 2: `define\\\_and\\\_compile\\\_model`



We define the simplest neural network using \*\*TensorFlow/Keras\*\*:

\* \*\*Architecture\*\*: A `Sequential` model with a single \*\*`Dense` layer\*\* and \*\*1 unit\*\*.

\* \*\*Input Shape\*\*: `shape=(1,)` since the feature ($\\mathbf{x}$, number of bedrooms) is a single scalar value.

\* \*\*Optimizer\*\*: \*\*`sgd`\*\* (Stochastic Gradient Descent).

\* \*\*Loss\*\*: \*\*`mean\\\_squared\\\_error`\*\* (MSE).



\### Exercise 3: `train\\\_model`



The model is trained by calling \*\*`model.fit()`\*\* for \*\*500 epochs\*\*, using the data generated in Exercise 1. This process minimizes the MSE loss, allowing the single neuron to learn the weights that represent the linear function ($0.5x + 0.5$).



---



\## ✅ Final Prediction



After training, the model is tested by predicting the price for a \*\*7-bedroom house\*\* ($x=7.0$).



```python

\\# Expected result should be close to 4.0 (which equals $400,000)

predicted\\\_price = trained\\\_model.predict(np.array(\\\[7.0])).item()

```

The final prediction should be very close to 4.0 (e.g., 4.005 or 3.998).

