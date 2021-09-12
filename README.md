# 🐶 Using Transfer Learning and TensorFlow 2.0 to Classify Different Dog Breeds

In this project we're going to be using machine learning to help us identify different breeds of dogs.

### Technologies and Methods Used
  * Python
  * Pandas, Numpy, Matplotlib
  * Google Collab, Google Cloud
  * GPU
  * Keras, Tensorflow
  * Deep Learning (Neural Networks), Transfer Learning
  * Data Visualization

To do this, we'll be using data from the [Kaggle dog breed identification competition](https://www.kaggle.com/c/dog-breed-identification/overview). It consists of a collection of 10,000+ labelled images of 120 different dog breeds.

This kind of problem is called multi-class image classification.

Since the most important step in a deep learning problem is getting the data ready (turning it into numbers), that's what we're going to start with.

We're going to go through the following TensorFlow/Deep Learning workflow:
1. Get data ready (download from Kaggle, store, import).
2. Prepare the data (preprocessing, the 3 sets, X & y).
3. Choose and fit/train a model ([TensorFlow Hub](https://www.tensorflow.org/hub), `tf.keras.applications`, [TensorBoard](https://www.tensorflow.org/tensorboard), [EarlyStopping](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks/EarlyStopping)).
4. Evaluating a model (making predictions, comparing them with the ground truth labels).
5. Improve the model through experimentation (start with 1000 images, make sure it works, increase the number of images).

For preprocessing our data, we're going to use TensorFlow 2.x. The whole premise here is to get our data into Tensors (arrays of numbers which can be run on GPUs) and then allow a machine learning model to find patterns between them.

For our machine learning model, we're going to use sequential API in Keras.

The first layer we use is the model from TensorFlow Hub (hub.KerasLayer(MODEL_URL). So our first layer is actually an entire model (many more layers). That input layer takes in the images and finds patterns in them based on the patterns mobilenet_v2_130_224 (chosen model for training) has found.

The next layer (tf.keras.layers.Dense()) is the output layer of my model. It brings all of the information discovered in the input layer together and outputs it in the shape we are after, 120 (the number of unique labels I had). In addition, we set the activation parameter to "softmax" that tells the output layer, I'd like to assign a probability value to each of the 120 labels somewhere between 0 & 1. The higher the value, the more the model believes the input image should have that label. 

Finally, after we compile the model and build it, we will train it and make predictions on test data.
