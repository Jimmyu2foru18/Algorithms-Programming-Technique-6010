# Chapter 1: Introduction — Building a Digit Recognition Network

1. PURPOSE OF THIS VIDEO

Welcome back. In today's video, we're going to build a neural
network that recognizes handwritten digits in Python.

2. MODERN REWORK

There's already an older video on this channel about handwritten
digit recognition in Python, but the quality is not good. This is
a modern rework because the topic is interesting, especially for
beginners into machine learning who want to learn the basics and
start with neural networks.

This is a good beginner project when it comes to working with
neural networks.

3. PROJECT OVERVIEW

What we're going to do:

- Load the MNIST data set from TensorFlow Keras.
- The data set contains handwritten digits in 28x28 pixel format
  with respective labels.
- Train a neural network with that data set.
- Test the model.
- Provide our own images (draw in Paint or scan actual handwritten
  digits, scale them down).
- Predict our own digits using the neural network.

4. LIBRARIES

The first thing is to install a bunch of libraries:

- numpy
- opencv-python (cv2)
- matplotlib
- tensorflow

And we'll also need the os module.

Library purposes:

- matplotlib: visualization of actual digits (optional).
- numpy: working with numpy arrays.
- cv2 (opencv-python): computer vision, loading and processing images.
- tensorflow: the machine learning part.

# Chapter 2: Setup and Libraries

1. INSTALLATION

Open command line (Windows) or terminal (Linux/Mac) and type:

```
pip install numpy opencv-python matplotlib tensorflow

```
2. IMPORTS

```
import cv2
import numpy as np
import matplotlib.pyplot as plt
import tensorflow as tf
import os

```
# Chapter 3: Loading the Dataset

1. LOADING MNIST

```
mnist = tf.keras.datasets.mnist

```
This loads the data set directly from TensorFlow without needing
to download CSV files and process them.

2. TRAINING AND TESTING SPLIT

Split the data into training data and testing data:

- Training data: what we use to train the model.
- Testing data: labeled data used to assess how well the model
  performs on data it has never seen before.

Usually an 80/20 split, but MNIST's load data function already
splits it into training and testing data.

```
(x_train, y_train), (x_test, y_test) = mnist.load_data()

```
- x: the pixel data (the image itself, the handwritten digit).
- y: the classification (the digit number).

3. PURPOSE OF SPLIT

Training data trains the model; testing data evaluates performance
on unseen data. This is the idea of testing and training.

# Chapter 4: Data Normalization

1. WHAT NORMALIZATION MEANS

Normalizing means scaling values down so every value is between
0 and 1.

A grayscale pixel can have a lightness from 0 to 255 (ignoring
RGB values). After normalization:

- 125 becomes around 0.5.
- All values are scaled between 0 and 1.

This makes it easier for a neural network to do calculations.

2. NORMALIZING THE DATA

```
x_train = tf.keras.utils.normalize(x_train, axis=1)
x_test = tf.keras.utils.normalize(x_test, axis=1)

```
Axis=1 means we normalize the pixels, not the digits.

3. PRE-PROCESSING COMPLETE

After normalization, all pre-processing is done. We can now start
working on the neural network.

# Chapter 5: Building the Model

1. CREATING THE MODEL

```
model = tf.keras.models.Sequential()

```
Sequential is the basic sequential neural network model.

2. ADDING LAYERS

Flatten layer:

```
model.add(tf.keras.layers.Flatten(input_shape=(28, 28)))

```
A flattened layer turns a 28x28 grid into one flat line of 784
pixels instead of having a grid.

Dense layer (hidden layer 1):

```
model.add(tf.keras.layers.Dense(128, activation='relu'))

```
- 128 units.
- ReLU activation (rectified linear unit): zero if negative,
  linear increase if positive.

Dense layer (hidden layer 2):

Same as above — another 128-unit ReLU dense layer.

Dense layer (output):

```
model.add(tf.keras.layers.Dense(10, activation='softmax'))

```
- 10 units representing digits 0-9.
- Softmax activation: makes all 10 outputs add up to 1,
  interpretable as confidence/probability for each digit.

Example: for an obvious 2, the third neuron (index 2) shows ~0.95,
and other neurons show low confidence.

3. NOTE ON THEORY

This video doesn't go deep into theory (activation functions,
optimizers, loss functions, layer types). It just builds and uses
the model.

# Chapter 6: Training the Model

1. COMPILING THE MODEL

```
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)

```
- Optimizer: adam.
- Loss function: sparse categorical cross entropy.
- Metric: accuracy.

2. FITTING (TRAINING) THE MODEL

```
model.fit(x_train, y_train, epochs=3)

```
- Epochs: how many times the model sees the same data over again.
- 3 epochs is enough for this task.

3. SAVING THE MODEL

```
model.save('handwritten.model')

```
Save after training so we don't need to retrain every time.

4. NOTE ON OVERKILL

A neural network is a bit overkill for handwritten digit
recognition — SVM or KNN could also accomplish this. But it's a
good beginner project. Convolutional neural networks with max
pooling would be even more professional but over the top.

5. TRAINING PROGRESS

Epoch 1 out of 3, etc. Training is fast.

# Chapter 7: Saving the Model

1. LOADING THE MODEL

Instead of retraining every time, load the saved model:

```
model = tf.keras.models.load_model('handwritten.model')

```
2. EVALUATING THE MODEL

```
loss, accuracy = model.evaluate(x_test, y_test)

```
- Low loss is good.
- High accuracy is good (1 = 100% accuracy).

Example results: loss ~0.09, accuracy ~97%. That means about 3%
were classified incorrectly. No model is perfect.

# Chapter 8: Model Evaluation

1. PRINTING METRICS

```
print(loss)
print(accuracy)

```
These metrics tell us how accurate our model is.

2. ACCURACY INTERPRETATION

Accuracy is a number between 0 and 1. One means 100% accuracy.
In this case, about 97% correct, ~3% incorrect.

# Chapter 9: Custom Digit Recognition

1. DRAWING CUSTOM DIGITS

Use Paint (or scan actual handwritten digits) to draw digits,
then scale them down to 28x28 pixels.

Steps in Paint:

- Resize to 28x28 pixels (uncheck maintain aspect ratio).
- Use a basic pencil, finest size.
- Write handwritten digits (e.g., 3, 5).
- Save in a directory (e.g., a "digits" folder with files named
  digit1.png, digit2.png, etc.).

2. LOADING AND PREDICTING CUSTOM DIGITS

Iterate through files:

```
image_number = 1
while os.path.isfile(f"digits/digit{image_number}.png"):
    image = cv2.imread(f"digits/digit{image_number}.png")
    image = np.invert(image)
    image = np.array([image])
    prediction = model.predict(image)
    print(f"This digit is probably {np.argmax(prediction)}")
    plt.imshow(image[0], cmap=plt.cm.binary)
    plt.show()
    image_number += 1

```
Key steps:

- cv2.imread: load the image.
- np.invert: invert the image (white on black -> black on white).
- np.array: make it an array in the right shape for the model.
- model.predict: get activations for all digit neurons.
- np.argmax: get the index of the field with the highest number
  (which neuron has highest activation).
- Neuron index 0 = digit 0, index 1 = digit 1, etc.
- plt.imshow with cmap=binary: show the image.

3. ERROR HANDLING

Wrap in try/except; if something fails, print "error" and continue.

4. RESULTS

Example predictions: 3 (correct), 7 (correct), 7 (correct), 8
(correct), 5 (correct), 9 (incorrect — first misclassification),
then 0, 1, 1, 2, 4, 4, 4 (all correct).

11 out of 12 correct = ~91% accuracy on custom digits.

5. IMPROVEMENT OPTIONS

- Train with more epochs.
- More training data.
- Restructure the neural network.
- Use convolutional neural networks with max pooling (overkill).

# Chapter 10: Conclusion

That's how you recognize handwritten digits using neural networks
in Python. Like, comment, and subscribe for more content.

# Final Review: Key Concepts

Concept / Term              Purpose or Definition
MNIST data set              Handwritten digits in 28x28 pixel format with labels
x_train / y_train           Training pixel data and labels
x_test / y_test             Testing pixel data and labels
Normalization               Scaling pixel values (0-255) to range [0, 1]
Flatten layer               Converts 28x28 grid to 784-pixel flat vector
Dense layer                 Basic fully connected neural network layer
ReLU activation             Zero if negative, linear if positive
Softmax activation          Outputs sum to 1; interpretable as probabilities
Adam optimizer              Optimization algorithm for training
Sparse categorical crossentropy Loss function for multi-class classification
Epochs                      Number of times model sees full training data
model.save / load_model     Save and reload trained model without retraining
model.evaluate              Compute loss and accuracy on test data
cv2.imread                  Load image file
np.invert                   Invert image colors
np.argmax                   Index of highest activation (predicted digit)
plt.imshow                  Display image with binary colormap

# Important Concepts to Remember

1. MNIST Data Set: Contains handwritten digits in 28x28 pixel format
   with labels, loaded via tf.keras.datasets.mnist.

2. Training vs Testing Split: Training data trains the model; testing
   data evaluates performance on unseen data. MNIST comes pre-split.

3. Normalization: Scaling pixel values from 0-255 to 0-1 range using
   tf.keras.utils.normalize with axis=1.

4. Flatten Layer: Converts 28x28 pixel grid into a 784-element flat
   vector for input to dense layers.

5. Dense Layer: Ful connected layer; hidden layers use 128 units with
   ReLU activation, output layer uses 10 units with softmax.

6. ReLU Activation: Rectified linear unit; outputs 0 for negative
   inputs, linear increase for positive inputs.

7. Softmax Activation: Ensures all 10 output neurons sum to 1,
   interpretable as confidence/probability per digit.

8. Model Compilation: Uses adam optimizer, sparse categorical
   crossentropy loss, and accuracy metric.

9. Training: model.fit(x_train, y_train, epochs=3); 3 epochs is
   sufficient for this task.

10. Saving/Loading: model.save() stores the trained model;
    tf.keras.models.load_model() reloads it without retraining.

11. Evaluation: model.evaluate(x_test, y_test) returns loss and
    accuracy; low loss and high accuracy are desired.

12. Custom Digit Prediction: Load image with cv2.imread, invert with
    np.invert, convert to array, predict with model.predict(),
    get predicted digit with np.argmax().

13. np.argmax: Returns the index of the highest activation value,
    which corresponds to the predicted digit (0-9).

14. Image Display: plt.imshow(image, cmap=plt.cm.binary) shows the
    digit image in binary colormap.

15. Error Handling: Use try/except when loading and predicting custom
    images to handle missing or malformed files gracefully.

# The Big Picture

```
                DIGIT RECOGNITION PIPELINE
                       |
         +-------------+-------------+
         |                           |
   LOAD MNIST                 PRE-PROCESS
```
   (x_train, y_train)         normalize pixels to [0, 1]
   (x_test, y_test)             tf.keras.utils.normalize
             |                           |
             v                           v
    BUILD MODEL                 TRAIN MODEL
   Sequential model            model.fit(epochs=3)
   Flatten -> Dense(128, ReLU)   adam optimizer
   Dense(128, ReLU)            sparse_categorical_crossentropy
   Dense(10, softmax)          accuracy metric
             |                           |
             v                           v
    SAVE MODEL                 EVALUATE MODEL
   model.save()               model.evaluate(x_test, y_test)
   load_model()               loss + accuracy
             |                           |
             +-------------+-------------+
                           |
                  CUSTOM DIGIT PREDICTION
                  cv2.imread -> np.invert -> predict
                  -> np.argmax -> display with plt

The central idea:

Build a simple sequential neural network in TensorFlow/Keras to
recognize handwritten digits. Load MNIST, normalize pixels, build
a Flatten-Dense-Dense-Dense model with ReLU and softmax, train
with Adam optimizer for 3 epochs, evaluate on test data, then use
the model to predict custom drawn digits.
