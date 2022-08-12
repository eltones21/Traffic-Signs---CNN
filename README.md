This project consists of the development of a model using convolutional neural network.

Background
As research continues in the development of self-driving cars, one of the key challenges is computer vision, allowing these cars to develop an understanding of their environment from digital images. In particular, this involves the ability to recognize and distinguish road signs – stop signs, speed limit signs, yield signs, and more.

In this project, you’ll use TensorFlow to build a neural network to classify road signs based on an image of those signs. To do so, you’ll need a labeled dataset: a collection of images that have already been categorized by the road sign represented in them.

Several such data sets exist, but for this project, we’ll use the German Traffic Sign Recognition Benchmark (GTSRB) dataset, which contains thousands of images of 43 different kinds of road signs.

Specification
The convolutional neural network model is based on the TensorFlow Keras Sequential Model.

traffic.py -  In the main function, we accept as command-line arguments a directory containing the data and (optionally) a filename to which to save the trained model. The data and corresponding labels are then loaded from the data directory (via the load_data function) and split into training and testing sets. After that, the get_model function is called to obtain a compiled neural network that is then fitted on the training data. The model is then evaluated on the testing data. Finally, if a model filename was provided, the trained model is saved to disk.

Model & Results

Various types of setting were utilized including
    different numbers of convolutional and pooling layers
    different numbers and sizes of filters for convolutional layers
    different numbers and sizes of hidden layers
    dropout

At first this setting was applied:
    1CNN layer(32 neurons) + 1 hidden layer(128 neurons) + 20% dropout 
    The result for this setting was loss: 0.3564 - accuracy: 0.8941

The accucary seemed very good but the loss could be improved.  A convolution layer was added increase performance.
    
    1 CNN layer(32 neurons) + 1 CNN layer(64 neurons) + 1 hidden layer (128 neurons) + 20% dropout 
    The result for this setting was, loss: loss: 0.1520 - accuracy: 0.9613

The result for this setting was improved with loss decreasing by hald and accuracy increasing by 8%. The next setting added a new hidden layer.

    1 CNN layer(32 neurons) + 1 CNN layer(64 neurons) + 1 hidden layer (128 neurons) + 1 hidden layer (128 neurons) + 20% dropout
    The result for this setting was, loss: 0.1113 - accuracy: 0.9724

There was another impromvent in loss and the accuracy but at this time less impactful. 

Lastly, after adding other convolutional layers, we noticed that not necessarily the model performance improved in terms of accuracy and loss. So, the conclusion is that the better performance model include 2 convolution layers (one with 32 and another with 64 filters and 3x3 kernels), 2 max-pooling layers (2x2), 2 hidden layer (128 neurons), and a 20% dropout in order to ensure the model does not overfit.
