# Video 7 Neural Network Python Project - Handwritten Digit Recognition Questions 
- **Q:** What libraries are needed to build the digit recognition neural network?

- **Q:** How is the MNIST data set loaded in TensorFlow/Keras?

- **Q:** What is the difference between training data and testing data?

- **Q:** What does normalization do to pixel values, and why is it done?

- **Q:** What does the Flatten layer do to a 28x28 pixel image?

- **Q:** What activation function is used in the hidden layers, and what does it do?

- **Q:** What activation function is used in the output layer, and what does it do?

- **Q:** How many output neurons are there, and what does each represent?

- **Q:** What optimizer and loss function are used when compiling the model?

- **Q:** How many epochs are used for training, and what does an epoch mean?

- **Q:** How do you save and reload a trained model?

- **Q:** How do you evaluate the model on test data?

- **Q:** How do you load and preprocess a custom drawn digit image?

- **Q:** How does np.argmax determine the predicted digit?

- **Q:** What was the accuracy on the custom digit test (11 out of 12)?

- libraries needed: numpy opencv-python matplotlib tensorflow

- mnist.load_data() split

- normalize axis=1

- Flatten 28x28 to 784

- Dense 128 ReLU hidden layers

- Dense 10 softmax output layer

- adam optimizer sparse_categorical_crossentropy

- epochs=3

- model.save / tf.keras.models.load_model

- model.evaluate x_test y_test

- cv2.imread np.invert np.argmax

- 11/12 custom digit accuracy
