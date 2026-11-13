What libraries are needed to build the digit recognition neural network?

How is the MNIST data set loaded in TensorFlow/Keras?

What is the difference between training data and testing data?

What does normalization do to pixel values, and why is it done?

What does the Flatten layer do to a 28x28 pixel image?

What activation function is used in the hidden layers, and what does it do?

What activation function is used in the output layer, and what does it do?

How many output neurons are there, and what does each represent?

What optimizer and loss function are used when compiling the model?

How many epochs are used for training, and what does an epoch mean?

How do you save and reload a trained model?

How do you evaluate the model on test data?

How do you load and preprocess a custom drawn digit image?

How does np.argmax determine the predicted digit?

What was the accuracy on the custom digit test (11 out of 12)?

libraries needed: numpy opencv-python matplotlib tensorflow

mnist.load_data() split

normalize axis=1

Flatten 28x28 to 784

Dense 128 ReLU hidden layers

Dense 10 softmax output layer

adam optimizer sparse_categorical_crossentropy

epochs=3

model.save / tf.keras.models.load_model

model.evaluate x_test y_test

cv2.imread np.invert np.argmax

11/12 custom digit accuracy
