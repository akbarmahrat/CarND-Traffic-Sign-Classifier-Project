# Traffic Sign Classifier [![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

 

### Solution file attached 
/Traffic_Sign_Classifier.ipynb

### Below Steps are followed
* Load the data set
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report



### Basic summary of the data set

Number of training examples = 34799
Number of testing examples = 12630
Image data shape = (32, 32, 3)
Number of classes = 43

### Exploratory visualization on the data set

total tests 34799. total labels: 43

Please see cell 6 results. 
Sign visualization file attached. 

### Design and Test a Model Architecture

#### Preprocessing

We reduced the color of sign images because it help in proccessing image faster and Signs are meant for day and night purpose so sign design is more important than the color of sign.  

My preprocessing phase 
1. normalizes images
2. grayscales images

Please see Cell 7 output.


#### Model Architecture
 
I used LeNet architecture as shown in classroom example with 2 convolutional neuronal network to classify the traffic signs. 
 
1. convolution 1: 32x32x1  -> 28x28x12 -> relu -> 14x14x12 (pooling)
2. convolution 2: 14x14x12 -> 10x10x25 -> relu -> 5x5x25   (pooling)
3.       flatten: 5x5x25   -> 625
4.        linear: 625      -> 300
5.        linear: 300      -> 150
6.        linear: 150      -> 43

#### Model Training
I used my local machine to train the model in 16 Epochs, and each Epochs is trained with 64 batch size. 
I used Adam optimizer with learning rate 0.001.

Here are my final training parameters:
* Epochs = 16
* Batch size = 64
* Learning rate = 0.001

My results were below after avlidation and training the model:
* Validation Accuracy = 91.5%
* Testing Accuracy = 90.8%


#### Solution Approach

I used the LeNet architecture as taught in the classroom. Initially I got accuracy of 80% in test so added a additional convolutional layer with learning rate 0.01 which improvised the accuracy about 90%. For further improvisation I tried 30 Epochs but I observed there was not much change after 12th epoch but decreased slightly. 
As I am testing on my local machine So I sticked it to 12 Epochs with learning rate 0.001 and got 90% accuracy in testing. Although it took lots of time to complete in my local machine so I will try to run it later on AWS.


### Test on new images

#### Acquiring New Images

I used google images and wikipedia page for Germany traffic signs to get new images for my testing set. 

#### Performance on New Images

The accuracy with new traffic signs downloaded from internet was 84.6%, while it was 90% on
the test set. clearly its underfitting because of low image quality. I will try few more techniques to improvise the quality of images.

#### Softmax Probabilities

The accuracy is 84.6%. it  predicted correctly 11 out of 13 images. I observed it struggles with speed limit signs.

By looking at the Top_V data I can say it have less accuracy for  speed signs. The predictions of speed limit 70km/h is wrong, it is pridicting as bumpy road.  If i include few more speed limit signs images like 20, 30, 50 then accuracy will go down.

I will think about the speed limit sign issues. I think I need to work on improvisation of preproccessing.

### Resources
* [Udacity Self Driving Nanodegree](http://www.udacity.com/drive)
* https://github.com/udacity/CarND-Traffic-Sign-Classifier-Project
* http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset
* https://en.wikipedia.org/wiki/Road_signs_in_Germany
