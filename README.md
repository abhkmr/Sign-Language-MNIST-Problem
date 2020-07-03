# Sign-Language-MNIST-Problem
A Hand Sign Recognition application using ASL MNIST Dataset(TensorFlow &amp; OpenCV)

<h1>Dataset Description</h1>
American Sign Language(ASL) is a complete, natural language that has the same linguistic properties as spoken languages, with grammar that differs from English. ASL is expressed by the movement of hands and faces. This dataset consists of 27,455 images of hand signs, each image is of 28 x 28 size and in grayscale format. The dataset format is patterned to match closely with the classic MNIST. Images in the dataset belong to a label from 0–25 representing letters from A-Z(but no cases of 9=J or 25=Z as they involve hand motion). The training data(27,455 cases) and the test data(7,172 cases) are approximately half the size of standard MNIST but otherwise similar to a header row of the label, pixel1, pixel….pixel784. The original hand gesture image data represented multiple users repeating gestures against different backgrounds. The Sign Language MNIST data came from greatly extending the small number (1704) of the color images included as not cropped around the hand region of interest. To create new data, an image pipeline was used based on ImageMagick and included cropping to hands-only, gray-scaling, resizing, and then creating at least 50+ variations to enlarge the quantity.


Hand SignsImporting Libraries
We'll start with importing necessary libraries which we will be using further in our application.
Importing LibrariesLoading Datasets and Preprocessing
We'll be using pandas to import and transform the data into a form that can be used in the model.
Previewing Dataset
Using pandas df.head() function we will be viewing few of the top rows of the training and testing dataset.
Statistical Analysis of Data
With train.describe(),train.info() & other various commands we will try to statistically visualize the data.
Data Visualization
Visualizing the first 10 images of the dataset.
Visualizing Data on the basis of the count of labels.
The dataset seems balanced as for each training label(except 9 an.d 25)Building Model
Step 1:- The first step involved in building our model is defining the learning Rate using Keras callbacks function ReduceLROnPlateau. Loss is being used for monitoring and if the loss is same for more than 2 epochs the learning will be described by a factor of 0.1.
learning_rate=keras.callbacks.ReduceLROnPlateau(monitor='accuracy',factor=0.1,patience=2,min_lr=0.0001)
Step 2:- Defining a sequential model to which we'll be adding several layers.
model = keras.models.Sequential()
Step 3:- Adding neural network layers to the sequential model.
Let's try to understand various layers of the model:- 
Conv2D:- This layer creates a convolution kernel that is convolved with the layer input to produce a tensor of outputs.
BatchNormalization:- Used to Normalise input and activations.
MaxPool2D:- Max pooling is a sample-based discretization process. The objective is to down-sample an input representation, reducing its dimensionality and allowing for assumptions to be made about features contained in the sub-regions binned.
Dropout:- Dropout is a technique used to prevent a model from overfitting. Dropout works by randomly setting the outgoing edges of hidden units to 0 at each update of the training phase
Flatten:- The Flatten layer is a layer that flattens an input to a simple vector output.
Dense:- Dense layer is the regular deeply connected neural network layer and performs {output = activation(dot(input, kernel) + bias)}.

Accuracy Report
We'll be using sklearn.metrics to get classification_report


Using OpenCV take input and show Result
Here we will be capturing video input into which the user will provide a hand sign. Video input from the user is passed on to the model created above which gives us the output to be displayed.
Accuracy ScoreHere we've built a simple hand recognition system with decent accuracy. Obviously, there is the scope of increasing accuracy and improving the quality of prediction. Here, I've tried to demonstrate a simple yet effective model that could be used further to build and improve upon.
